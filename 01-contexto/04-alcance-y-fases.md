# Alcance y fases

## Alcance del proyecto

El proyecto incluye el diseño y despliegue de una infraestructura perimetral virtualizada, la implementación de un SOC, la monitorización de servicios y la notarización blockchain de alertas críticas.

## Fase 1: Infraestructura y redes

- Creación de máquinas virtuales en Proxmox.
- Separación entre red de gestión y DMZ.
- Configuración de DHCP mediante ISC-DHCP.
- Configuración de DNS mediante Pi-hole.
- Aplicación de reglas de filtrado con iptables.

## Fase 2: SOC e IDS

- Instalación y configuración de Wazuh Server y Agents.
- Instalación y configuración de Suricata IDS.
- Creación de reglas de detección.
- Análisis y documentación de alertas.

## Fase 3: Hosting y aplicación

- Configuración de Nginx como servidor web.
- Despliegue de una aplicación con HTML y CSS.
- Configuración de la base de datos MySQL.
- Protección del servidor y de los servicios publicados.

## Fase 4: Monitorización y blockchain

- Configuración de Prometheus y Grafana.
- Creación de scripts en Bash y Python.
- Integración con Web3.
- Despliegue de un Smart Contract en Ethereum Testnet.
- Notarización de alertas críticas.

## Fase 5: Validación

- Simulación controlada de ataques de inyección SQL y DoS.
- Comprobación de la detección por parte del SOC.
- Verificación del registro inmutable de eventos.
- Documentación de resultados y evidencias.

## Fuentes y referencias

- [Añadir fuente o documentación]
- [Añadir artículo o guía]
- [Añadir captura o evidencia]