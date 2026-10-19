# Contexto del proyecto

[Volver a la portada](../README.md)

## Índice

- [Objetivo principal](#objetivo-principal)
- [Quiénes somos](#quiénes-somos)
- [Problema que resuelve](#problema-que-resuelve)
- [Alcance y fases](#alcance-y-fases)

## Objetivo principal

Implementar una infraestructura perimetral robusta, virtualizada y segura mediante Proxmox, capaz de detectar, monitorizar y registrar incidentes de seguridad. El SOC centralizado con Wazuh y Suricata analizará eventos y generará alertas. Se prevé notarizar los eventos críticos mediante un Smart Contract en Ethereum Testnet.

### Objetivos específicos

- Aislar la red de gestión de la DMZ de hosting.
- Desplegar DHCP y DNS con configuraciones seguras.
- Implementar un SOC centralizado con Wazuh y Suricata.
- Monitorizar la infraestructura mediante Prometheus y Grafana.
- Automatizar tareas mediante Bash y Python.
- Notarizar alertas críticas en Ethereum Testnet.
- Validar el sistema mediante simulaciones controladas en el laboratorio.

### Resultado esperado

Una plataforma de monitorización y auditoría de seguridad perimetral con detección de amenazas web y trazabilidad de eventos críticos. Este documento describe objetivos previstos, no resultados ya obtenidos.

## Quiénes somos

SecChain SOC Solutions está formado por Pau Toledano Tortajada, Luis Alberto Rodríguez Aguilar y Deivid Arley Cardona Pérez.

| Integrante | Habilidades e intereses | Compromiso |
|---|---|---|
| Pau Toledano Tortajada | Automatización, Prometheus/Grafana, DLT, contratos inteligentes y scripting | Integración del Smart Contract en Testnet para la notarización de logs críticos |
| Luis Alberto Rodríguez Aguilar | Nginx, bases de datos, SIEM/IDS, hardening y análisis de logs | Documentar las reglas de Wazuh y Suricata implementadas |
| Deivid Arley Cardona Pérez | Bash, PowerShell, hardening Linux y contenedores, CIS/INCIBE, Lynis, Docker Bench, coordinación e IA aplicada | Entregar avances semanales de hardening y scripts, documentarlos en GitHub y revisar el código del equipo |

Roles de aula: Pau es secretario, Luis supervisor y Deivid portavoz. La supervisión técnica principal rota según la fase activa.

[Ver organización y seguimiento del equipo](../04-equipo/README.md).

## Problema que resuelve

La propuesta aborda la detección de amenazas contra servicios web, la dispersión de registros entre distintos sistemas y la necesidad de conservar evidencias que permitan comprobar cambios posteriores.

### Solución propuesta

- Centralizar eventos y alertas mediante el SOC.
- Analizar sistemas y tráfico de red con Wazuh y Suricata.
- Monitorizar el estado de la infraestructura.
- Aportar trazabilidad adicional mediante notarización blockchain.
- Facilitar la auditoría y la validación de las pruebas.

El mecanismo exacto de notarización, los datos a registrar y sus límites se concretarán durante la investigación.

## Alcance y fases

La planificación siguiente organiza el trabajo documental; queda pendiente contrastar su numeración con la planificación definitiva del equipo.

### Fase 1: Infraestructura y redes

- Creación de máquinas virtuales en Proxmox.
- Separación entre red de gestión y DMZ.
- DHCP mediante ISC-DHCP y DNS mediante Pi-hole.
- Reglas de filtrado con iptables.

### Fase 2: SOC e IDS

- Instalación de Wazuh Server y Agents y Suricata IDS.
- Creación de reglas de detección.
- Análisis y documentación de alertas.

### Fase 3: Hosting y aplicación

- Configuración de Nginx.
- Aplicación con HTML y CSS y base de datos MySQL.
- Protección del servidor y los servicios publicados.
- Pendiente definir el componente de servidor que conectará la aplicación con MySQL.

### Fase 4: Monitorización y blockchain

- Configuración de Prometheus y Grafana.
- Scripts en Bash y Python e integración con Web3.
- Smart Contract en Ethereum Testnet y notarización de eventos críticos.

### Fase 5: Validación

- Simulación controlada de SQLi y DoS únicamente en el laboratorio autorizado.
- Comprobación de detección y trazabilidad.
- Documentación de resultados y evidencias.

## Fuentes y documentación

Base documental: Proyecto-pacto-de-socios.docx, aportado por el equipo. Las fuentes técnicas y evidencias se incorporarán durante la investigación.

[Volver a la portada](../README.md)
