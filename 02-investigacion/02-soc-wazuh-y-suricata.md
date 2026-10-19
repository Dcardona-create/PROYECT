# SOC, Wazuh y Suricata

## SOC

Un SOC, o *Security Operations Center*, es un centro de operaciones de seguridad. Su función es supervisar la infraestructura, detectar incidentes, analizar alertas y responder ante posibles amenazas.

En este proyecto, el SOC permitirá centralizar la información de seguridad generada por los servidores y dispositivos de la red.

## Wazuh

Wazuh es una plataforma de seguridad que permite recopilar logs, detectar amenazas, monitorizar la integridad de los sistemas y generar alertas.

Consta principalmente de:

- **Wazuh Server:** centraliza y analiza la información recibida.
- **Wazuh Agents:** se instalan en los equipos monitorizados.
- **Wazuh Indexer y Dashboard:** permiten almacenar, buscar y visualizar los datos.

## Suricata

Suricata es un sistema de detección de intrusiones, conocido como IDS. Analiza el tráfico de red para identificar actividades sospechosas, ataques o comportamientos anómalos.

Puede detectar actividades como:

- Escaneos de puertos.
- Tráfico malicioso.
- Ataques web.
- Intentos de explotación de vulnerabilidades.
- Tráfico relacionado con malware.

## Función en el proyecto

- Centralizar los eventos de seguridad.
- Detectar amenazas en los sistemas y en la red.
- Generar alertas ante incidentes relevantes.
- Analizar ataques simulados, como inyección SQL o DoS.
- Seleccionar alertas críticas para su notarización blockchain.

## Puntos para investigar

- Arquitectura de Wazuh.
- Instalación de Wazuh Server y Agents.
- Reglas y alertas de Wazuh.
- Funcionamiento de Suricata.
- Diferencias entre HIDS y NIDS.
- Análisis de logs y alertas.

## Fuentes y referencias

- [Añadir fuente o documentación]
- [Añadir artículo o guía]
- [Añadir captura o evidencia]