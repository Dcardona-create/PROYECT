# Investigación: DNS

## 1. ¿Qué es DNS?

El **Sistema de Nombres de Dominio** (DNS, por sus siglas en inglés) es el servicio que traduce nombres de dominio, como `ejemplo.com`, en direcciones IP, como `93.184.216.34`.

Su función principal es permitir que los usuarios accedan a páginas web y servicios mediante nombres fáciles de recordar, sin necesidad de conocer las direcciones IP de cada servidor.

Por ejemplo, cuando se accede a `google.com`, el equipo consulta al DNS para obtener la dirección IP del servidor de Google y poder establecer la conexión.

## 2. Funcionamiento de una consulta DNS

Cuando un usuario escribe un nombre de dominio en el navegador, se produce un proceso de resolución DNS:

1. El dispositivo consulta al servidor DNS configurado, normalmente el DNS local o el proporcionado por el proveedor.
2. Si el servidor no conoce la respuesta, consulta a los servidores raíz.
3. Los servidores raíz indican qué servidor gestiona el dominio de primer nivel, como `.com`.
4. El servidor TLD indica el servidor autoritativo del dominio.
5. El servidor autoritativo responde con la dirección IP solicitada.
6. La respuesta se guarda en caché durante un tiempo determinado para acelerar futuras consultas.

### Elementos principales

| Elemento | Función |
|---|---|
| Resolver | Cliente o servidor que realiza la consulta DNS |
| Servidor raíz | Indica los servidores responsables de los TLD |
| Servidor TLD | Gestiona dominios como `.com`, `.es` o `.org` |
| Servidor autoritativo | Contiene la información oficial de un dominio |
| Caché DNS | Guarda respuestas temporales para acelerar consultas |

## 3. Tipos de registros DNS

Los registros DNS almacenan información sobre un dominio y permiten que los servicios funcionen correctamente.

| Registro | Función |
|---|---|
| A | Asocia un dominio con una dirección IPv4 |
| AAAA | Asocia un dominio con una dirección IPv6 |
| CNAME | Asigna un alias a otro nombre de dominio |
| MX | Indica los servidores responsables del correo electrónico |
| NS | Identifica los servidores DNS autoritativos de un dominio |
| PTR | Realiza la resolución inversa: de IP a nombre de dominio |
| TXT | Almacena información de texto, como verificaciones o políticas de seguridad |
| SOA | Contiene información administrativa de la zona DNS |

## 4. Tipos de servidores DNS

### DNS recursivo

El servidor DNS recursivo realiza las consultas necesarias para obtener la respuesta final. Es el servidor al que suelen consultar los dispositivos de una red.

### DNS autoritativo

El servidor autoritativo contiene la información oficial de un dominio y responde con los registros correspondientes.

### DNS forwarder

Un DNS forwarder recibe consultas y las reenvía a otro servidor DNS, normalmente uno externo o más rápido.

### DNS local

Un DNS local resuelve nombres internos de una red, como `servidor.local` o `web.dmz`, sin depender completamente de servidores externos.

## 5. DNS en el proyecto

En el proyecto **SecChain SOC Solutions**, Pi-hole se utilizará como servicio DNS para mejorar el control, la privacidad y la seguridad del tráfico DNS.

Pi-hole permitirá:

- Resolver nombres de dominio dentro de la red.
- Filtrar dominios publicitarios y maliciosos.
- Registrar las consultas DNS realizadas por los dispositivos.
- Reducir el acceso a dominios peligrosos.
- Apoyar la configuración de los servicios alojados en la DMZ.

## 6. Seguridad en DNS

DNS puede ser utilizado por atacantes para ocultar comunicaciones maliciosas. Uno de los ejemplos más conocidos es el **DNS Tunneling**.

### DNS Tunneling

El DNS Tunneling permite enviar información dentro de consultas DNS. Un atacante puede utilizar registros DNS para extraer datos de una red o establecer un canal de comunicación encubierto.

Por este motivo, es importante monitorizar las consultas DNS, detectar patrones anómalos y limitar el acceso a dominios desconocidos o sospechosos.

### Buenas prácticas

- Utilizar un servidor DNS controlado, como Pi-hole.
- Monitorizar las consultas DNS realizadas por los equipos.
- Bloquear dominios maliciosos o no necesarios.
- Mantener actualizados los filtros y listas de bloqueo.
- Analizar alertas relacionadas con tráfico DNS anómalo.
- Limitar las consultas DNS externas desde la DMZ.

## 7. Actividades relacionadas

Esta investigación se relaciona directamente con las siguientes actividades:

| Actividad | Tema | Enlace |
|---|---|---|
| ACT1 | Seguridad en DNS: DNS Tunneling | [Ver actividad](https://github.com/deivid-cardona/Actividades-ASIXII/tree/main/ACT1-dns-tunneling) |
| ACT2 | Análisis y resolución del sistema DNS | [Ver actividad](https://github.com/deivid-cardona/Actividades-ASIXII/tree/main/ACT2-dns-resolucion) |

## 8. Imágenes y evidencias

En esta sección se añadirán capturas de las prácticas y pruebas realizadas.

### Consulta DNS

![Consulta DNS](imagenes/consulta-dns.png)

### Pi-hole

![Pi-hole](imagenes/pihole.png)

### DNS Tunneling

![DNS Tunneling](imagenes/dns-tunneling.png)

> Sustituir las rutas anteriores por las capturas reales cuando se añadan al repositorio.

## 9. Fuentes y referencias

- [Añadir documentación oficial de Pi-hole]
- [Añadir documentación sobre DNS]
- [Añadir artículo sobre DNS Tunneling]
- [Añadir guía de seguridad DNS]
- [Añadir captura o evidencia]