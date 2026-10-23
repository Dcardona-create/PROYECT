# Proxmox VE — Virtualización, clúster y redes de laboratorio

Investigación técnica de HOSTLOCK y base para la actividad de Proxmox. **Estado:** fundamentos y diseño propuesto. Configuración real, comandos definitivos y evidencias pendientes; no representa un despliegue completado.

## Objetivo y contexto

Comprender la administración de máquinas virtuales, contenedores, almacenamiento, usuarios y redes con Proxmox VE. En HOSTLOCK se contempla como infraestructura para alojar los servicios del laboratorio. La actividad comprende fundamentos, creación de un clúster, una práctica de router en VirtualBox/VMware y otra con LXC, Alpine Linux y Nginx en Proxmox.

Esta documentación desarrolla Proxmox dentro del apartado existente de infraestructura. Las investigaciones de hardening y filtrado podrán ampliarse posteriormente sin cambiar esta ubicación. Las relaciones con otras investigaciones se decidirán más adelante.

## Plataforma e hipervisores

Proxmox VE es una plataforma de virtualización de código abierto basada en Debian GNU/Linux. Integra máquinas virtuales QEMU/KVM y contenedores LXC, con administración web, API y línea de comandos.

Un hipervisor administra los recursos de las máquinas virtuales. Los de tipo 1 trabajan sobre la infraestructura del servidor; ejemplos: VMware ESXi, Microsoft Hyper-V y KVM en una plataforma dedicada como Proxmox. Los de tipo 2 funcionan sobre un sistema anfitrión de escritorio; ejemplos: VirtualBox y VMware Workstation. Proxmox se apoya en KVM integrado en el kernel Linux, no en un hipervisor de escritorio de tipo 2.

| Componente | Función |
|---|---|
| QEMU | Modelo de máquina virtual, dispositivos virtualizados y capacidades de emulación |
| KVM | Virtualización asistida por hardware integrada en el kernel Linux |
| LXC | Contenedores Linux que comparten el kernel del host |
| noVNC | Consola VNC desde el navegador; no es un hipervisor |
| Ceph | Almacenamiento distribuido integrable con Proxmox |

QEMU y KVM trabajan conjuntamente para ejecutar las VM. Una VM dispone de kernel propio; un contenedor LXC comparte el kernel del host. Para la práctica se plantea una VM Alpine con Nginx y un contenedor Linux como router.

## Clúster de Proxmox

Un clúster agrupa nodos Proxmox para administrarlos conjuntamente. `pvecm` administra el clúster, Corosync mantiene la comunicación y pertenencia y `pmxcfs` distribuye su configuración. No combina automáticamente la RAM de los nodos ni convierte discos locales en almacenamiento compartido.

### Quorum y alta disponibilidad

El quorum requiere una mayoría de votos para permitir cambios seguros y evitar decisiones contradictorias entre particiones. Se recomiendan al menos tres nodos para un quorum fiable. Dos nodos pueden apoyarse en un QDevice externo como voto adicional; este no proporciona recursos para ejecutar invitados.

La alta disponibilidad necesita quorum estable, comunicaciones fiables, capacidad en los nodos restantes, disponibilidad de discos y recursos configurados en el gestor HA. El fencing basado en watchdog ayuda a impedir ejecuciones incompatibles. Reiniciar un recurso en otro nodo no garantiza continuidad sin interrupción de la aplicación ni sustituye una copia de seguridad.

### Emulación del clúster

Se pueden ejecutar varios nodos Proxmox como VM sobre otro hipervisor: es virtualización anidada. Para ejecutar invitados KVM dentro de esos nodos deben exponerse las extensiones de virtualización y comprobarse la compatibilidad del procesador y del hipervisor exterior.

Varios nodos virtuales sobre un solo ordenador permiten practicar procedimientos, pero no ofrecen redundancia física frente al fallo de ese ordenador.

## Almacenamiento: ISO, plantillas y Ceph

Los almacenamientos se definen en `/etc/pve/storage.cfg`. Cada backend admite determinados contenidos: discos de VM, volúmenes de contenedores, ISO, plantillas LXC o copias de seguridad.

En el almacenamiento de directorio `local` con su ruta habitual:

```text
/var/lib/vz/template/iso/      Imágenes ISO
/var/lib/vz/template/cache/    Plantillas LXC
```

Las rutas dependen de la configuración. No representan la ubicación de todos los discos de invitados. `local-lvm` no es un directorio destinado a subir ISO.

Ceph proporciona almacenamiento distribuido: RBD ofrece bloques para discos de invitados y CephFS un sistema de archivos distribuido. Las políticas determinan distribución y redundancia. Ceph requiere recursos de discos, RAM y red; no es obligatorio para crear un clúster y no sustituye las copias de seguridad independientes.

## Usuarios, grupos y roles

Proxmox aplica permisos mediante usuarios, grupos, roles y ACL sobre rutas de recursos. Incluye roles como `Administrator`, `PVEAdmin`, `PVEVMAdmin`, `PVEVMUser` y `PVEAuditor`; sus privilegios deben comprobarse en la versión utilizada. La autenticación puede proceder de PAM, del servidor propio de Proxmox o de fuentes externas como LDAP y Active Directory.

Para HOSTLOCK se propone separar administración de infraestructura, operación de invitados, consulta y automatización con tokens API limitados. Estos perfiles son propuestas: no representan cuentas creadas.

## Propuesta de laboratorio

### Recursos de ejemplo

Dimensionamiento orientativo para un laboratorio básico sin Ceph; no son requisitos oficiales ni hardware confirmado:

| Elemento | CPU | RAM | Disco |
|---|---|---|---|
| Cada nodo pve1, pve2 y pve3 | 2–4 vCPU | 4–8 GB | 40–80 GB |
| Router LXC | 1 vCPU | 512 MB–1 GB | 4–8 GB |
| Alpine con Nginx | 1 vCPU | 512 MB–1 GB | 4–8 GB |

Los invitados consumen los recursos asignados a los nodos. Registrar CPU física, RAM, discos, virtualización disponible, hipervisor exterior si lo hay y versión real de Proxmox antes de desplegar.

### Preparación y creación del clúster

1. Instalar los nodos y fijar nombres e IP definitivos.
2. Comprobar conectividad y sincronización de hora.
3. Revisar versiones, almacenamiento y requisitos de comunicación.
4. Incorporar nodos antes de crear invitados en ellos: la unión sustituye la configuración de `/etc/pve` del nodo que se incorpora.

En el primer nodo, usando un nombre de ejemplo:

```bash
pvecm create HOSTLOCK-LAB
pvecm status
```

En cada nodo adicional, sustituyendo el identificador por la IP real:

```bash
pvecm add IP_DEL_NODO_EXISTENTE
```

Verificación:

```bash
pvecm nodes
pvecm status
systemctl status corosync --no-pager
```

Registrar miembros, IP y estado del quorum. Son instrucciones previstas, no resultados ya obtenidos.

## Redes e IPTables

### Práctica en VirtualBox o VMware

Crear dos VM: un router con una interfaz exterior y otra interior, y un cliente conectado únicamente a la red interna. El cliente utilizará la IP interior del router como puerta de enlace. Configurar encaminamiento, filtrado y NAT cuando la red exterior no tenga ruta de retorno. Documentar tanto la configuración como la prueba de salida a Internet.

Esta práctica es distinta de la implementación posterior en Proxmox y debe conservar sus propias evidencias.

### Red interna en Proxmox

```text
Equipo externo del laboratorio
             |
      Red externa / WAN
             |
           vmbr0
             |
   LXC router (WAN y LAN)
             |
           vmbr1
             |
     VM Alpine — Nginx
```

Los bridges Linux conectan interfaces virtuales. Un bridge sin puerto físico puede crear una red interna del nodo. El mismo nombre de bridge en distintos nodos no crea por sí solo una red común: para la práctica inicial, router y Alpine pueden alojarse en el mismo nodo. Extender la red entre nodos requiere diseño adicional.

Antes de configurar, definir IP/máscara WAN, gateway exterior, IP/máscara LAN, IP de Alpine, DNS, interfaces reales y puerto publicado. La puerta de enlace de Alpine será la IP LAN del router. Evitar solapamientos con otras redes.

El router LXC comparte el kernel del host. Revisar que dispone de las capacidades y funciones de red necesarias; no desactivar el aislamiento ni convertir el contenedor en privilegiado como primera solución ante un error.

### Configuración de red y Netplan

Proxmox utiliza habitualmente la interfaz web y `/etc/network/interfaces`, no Netplan por defecto. Alpine y el LXC utilizarán el mecanismo correspondiente a su sistema. Documentar Netplan solo en las máquinas que realmente lo usen, por ejemplo una VM Ubuntu configurada así.

Registrar bridges, puertos físicos, interfaces de invitados, direcciones, rutas, DNS y archivos reales de configuración. No presentar el mismo YAML como configuración nativa de todos los sistemas.

### Reglas y publicación web

Para salida a Internet: habilitar encaminamiento IPv4 en el router, establecer rutas y permitir el tráfico autorizado. Añadir NAT de salida si no existe una ruta externa de retorno a la LAN. Para acceder a Nginx desde la WAN del laboratorio: definir DNAT al puerto de la VM y permitir el tráfico reenviado.

| Elemento | Función |
|---|---|
| FORWARD | Filtrado del tráfico que atraviesa el router |
| PREROUTING | DNAT antes de decidir el encaminamiento |
| POSTROUTING | Traducción de origen en la salida |
| MASQUERADE | NAT de origen con la dirección de la interfaz de salida |
| DNAT | Cambio de dirección o puerto de destino |
| Seguimiento de conexiones | Gestión de conexiones y respuestas autorizadas |

Las reglas completas se redactarán con las direcciones e interfaces reales. Se aplicarán al router de la práctica, sin vaciar las reglas del host Proxmox. Registrar persistencia tras reiniciar. Si se utiliza OpenWrt, documentar su mecanismo de configuración sin mezclar instrucciones incompatibles.

Instalar Nginx en Alpine, comprobar el servicio y su página desde la LAN y después desde un equipo realmente externo a la red interna, usando el puerto publicado del router. La instalación y los comandos definitivos quedan pendientes de la versión y topología confirmadas.

## Pruebas y evidencias pendientes

| Apartado | Qué debe documentarse | Estado |
|---|---|---|
| Hardware | CPU, RAM, almacenamiento y virtualización | Pendiente |
| Clúster | Miembros, IP, pvecm nodes, pvecm status y quorum | Pendiente |
| VirtualBox/VMware | Router, cliente, reglas y salida a Internet | Pendiente |
| Red Proxmox | Bridges, interfaces, direcciones, rutas y DNS | Pendiente |
| Router LXC | Encaminamiento, reglas, contadores y persistencia | Pendiente |
| Alpine y Nginx | Instalación, servicio y prueba desde LAN | Pendiente |
| Acceso exterior | Página accesible desde WAN del laboratorio | Pendiente |
| Incidencias | Diagnóstico, corrección y comprobación posterior | Pendiente |

Se incorporarán capturas y salidas reales junto al procedimiento. No se presentan resultados inventados ni imágenes como si acreditaran pruebas aún no realizadas.

## Incidencias técnicas

Guía de diagnóstico; no es un registro de problemas ya observados:

| Síntoma | Revisar |
|---|---|
| Nodo no se incorpora | IP, conectividad, hora, versiones y servicios |
| Sin quorum | Miembros y comunicación de Corosync |
| Invitado anidado no inicia con KVM | Exposición de virtualización por hardware |
| Alpine no alcanza el router | Bridge, conexión virtual, interfaz y máscara |
| Sin Internet | Gateway, DNS, forwarding, filtro y NAT |
| Web funciona dentro pero no fuera | DNAT, FORWARD, ruta de retorno y filtros |
| Reglas se pierden al reiniciar | Persistencia y orden de carga |

Corosync necesita una comunicación estable y de baja latencia. Evitar competencia con tráfico intenso cuando sea posible. Cada incidencia real tendrá síntoma, diagnóstico, causa, cambio aplicado y evidencia posterior.

## Retirada de nodos y desmantelamiento

Retirar un nodo no elimina ni protege automáticamente sus invitados o datos. Debe planificarse:

1. Migrar o respaldar VM y contenedores; conservar datos locales.
2. Revisar HA, replicación, almacenamiento, Ceph y QDevice si existen. Si hay QDevice, seguir el procedimiento oficial de retirada antes de modificar miembros.
3. Apagar y aislar el nodo que se retira para impedir que vuelva con su configuración antigua.
4. Desde otro nodo con quorum, utilizar el nombre real:

```bash
pvecm delnode NOMBRE_DEL_NODO
pvecm nodes
pvecm status
```

5. Revisar referencias residuales y conservar la configuración necesaria antes de limpiarlas. Reinstalar el nodo antes de reutilizarlo o reincorporarlo es el método recomendado.

Para desmantelar el laboratorio completo, respaldar o trasladar primero los servicios y retirar dependencias. Planificar la secuencia según el quorum. No forzar votos como solución habitual a particiones de red. Restaurar snapshots previos o reinstalar es una opción de laboratorio cuando los datos necesarios ya estén protegidos. Consultar el procedimiento oficial antes de cualquier operación destructiva.

## Estado del trabajo

La base teórica y el diseño están documentados. Faltan hardware real, versiones, direcciones, configuraciones completas, instalación de servicios, ejecución, incidencias observadas y evidencias. No es una actividad terminada únicamente a falta de imágenes. La comprobación práctica en el aula forma parte de la evaluación.

## Fuentes oficiales

- [Guía de administración de Proxmox VE](https://pve.proxmox.com/pve-docs/pve-admin-guide.html)
- [Gestión del clúster](https://pve.proxmox.com/wiki/Cluster_Manager)
- [Configuración de red](https://pve.proxmox.com/wiki/Network_Configuration)
- [Almacenamiento](https://pve.proxmox.com/wiki/Storage)
- [Características de Proxmox VE](https://www.proxmox.com/en/products/proxmox-virtual-environment/features)
