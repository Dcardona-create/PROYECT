# PROYECT — SecChain SOC Solutions

## Nombre del equipo

**SecChain SOC Solutions**

## Integrantes

- Pau Toledano Tortajada
- Luis Alberto Rodríguez Aguilar
- Deivid Arley Cardona Pérez

## Objetivo principal

Implementar una infraestructura perimetral segura y virtualizada mediante Proxmox, desplegar un Centro de Operaciones de Seguridad (SOC) con Wazuh y Suricata, y registrar de forma inmutable las alertas críticas de seguridad mediante un Smart Contract en Ethereum Testnet.

## Contexto del proyecto

El proyecto busca proteger los servicios web de una organización mediante una red segmentada, monitorización centralizada, detección de intrusiones y trazabilidad inmutable de los eventos de seguridad más importantes.

La infraestructura incluirá una red de gestión aislada y una DMZ para el hosting de servicios. El SOC permitirá centralizar los registros, detectar amenazas y generar alertas; posteriormente, los eventos críticos se notarizarán en una red blockchain de pruebas.

## Fases del proyecto

1. Infraestructura virtualizada y configuración de redes.
2. Despliegue del SOC con Wazuh y Suricata.
3. Hosting web, base de datos y aplicación.
4. Monitorización, notarización blockchain y automatización.
5. Simulación controlada de ataques, validación y documentación final.

## Aplicativos previstos

- Proxmox VE
- ISC-DHCP
- Pi-hole
- iptables
- Nginx
- MySQL
- HTML y CSS
- Wazuh Server y Agents
- Suricata IDS
- Prometheus
- Grafana
- Python y Bash
- Web3
- Ethereum Testnet

## Estructura del repositorio

| Apartado | Tipo de contenido | Qué encontrarás | Acceso |
|---|---|---|---|
| Contexto del proyecto | Presentación y objetivos | Objetivo principal, problema que resuelve y alcance | [Ver contexto](./01-contexto/) |
| Investigaciones | Documentación técnica | DNS, DHCP, SOC, seguridad y blockchain | [Ver investigaciones](./02-investigacion/README.md) |
| Aplicativos | Herramientas y tecnologías | Aplicativos previstos y función dentro del proyecto | [Ver aplicativos](./03-aplicativos/) |
| Equipo | Organización y seguimiento | Integrantes, responsabilidades y avances semanales | [Ver equipo](./04-equipo/) |

## Autoría

Proyecto desarrollado por el equipo **SecChain SOC Solutions**.