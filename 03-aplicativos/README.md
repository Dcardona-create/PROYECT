# Aplicativos y tecnologías

[Volver a la portada](../README.md)

## Herramientas previstas y función

Esta página reúne el catálogo y la explicación de las herramientas del proyecto. Se trata de tecnologías previstas, no de despliegues completados.

### Virtualización

| Herramienta | Función prevista |
|---|---|
| Proxmox VE | Crear y administrar las máquinas virtuales y contenedores de la infraestructura; organizar la separación entre gestión y DMZ |

### Redes

| Herramienta | Función prevista |
|---|---|
| ISC-DHCP | Asignar direcciones IP y parámetros de red a los equipos |
| Pi-hole | Gestionar consultas DNS, registros locales y filtrado por listas configuradas |
| iptables | Definir reglas para controlar el tráfico entre redes y servicios |

### Hosting y aplicación

| Tecnología | Función prevista |
|---|---|
| Nginx | Publicar los servicios web y gestionar su acceso según la configuración |
| MySQL | Almacenar los datos de la aplicación; el modelo de datos está pendiente de definir |
| HTML y CSS | Crear la estructura y presentación de la interfaz web |

Pendiente de decisión: tecnología de servidor para conectar la aplicación con MySQL.

### Seguridad SOC

| Herramienta | Función prevista |
|---|---|
| Wazuh Server y Agents | Recopilar y analizar eventos de seguridad de los equipos y generar alertas |
| Suricata IDS | Analizar tráfico de red y generar alertas según las reglas y la visibilidad disponibles |

### Monitorización y blockchain

| Tecnología | Función prevista |
|---|---|
| Prometheus | Recopilar métricas de infraestructura y servicios mediante las integraciones que se configuren |
| Grafana | Mostrar métricas en paneles de seguimiento |
| Python y Bash | Automatizar tareas e integrar componentes |
| Web3 | Interactuar con la blockchain desde la integración que se desarrolle |
| Ethereum Testnet | Entorno de pruebas para el Smart Contract y la notarización de eventos críticos |

## Herramientas de apoyo al hardening

En el pacto se mencionan PowerShell, guías CIS/INCIBE, Lynis y Docker Bench como conocimientos y recursos del equipo. Su aplicación concreta se documentará al definir las tareas de auditoría y seguridad en contenedores.

## Decisiones pendientes

- Versiones y requisitos de cada herramienta.
- Arquitectura e integraciones entre componentes.
- Testnet y mecanismo de notarización.
- Justificación técnica y fuentes oficiales verificadas.

[Ver investigaciones](../02-investigacion/README.md) · [Volver a la portada](../README.md)
