# SOC, Wazuh y Suricata

Estado: borrador inicial conservado para revisión técnica y ampliación de fuentes.

[Volver al cuadro de investigaciones](../README.md)

## SOC

Un SOC, o Security Operations Center, supervisa la infraestructura, analiza alertas y coordina la respuesta ante posibles amenazas. En el proyecto se prevé centralizar la información de seguridad de servidores y dispositivos.

## Wazuh

El borrador contempla Wazuh para recopilar logs, detectar amenazas, monitorizar integridad y generar alertas.

- Wazuh Server: centralización y análisis.
- Wazuh Agents: recopilación en los equipos monitorizados.
- Wazuh Indexer y Dashboard: almacenamiento, búsqueda y visualización.

## Suricata

Se prevé utilizar Suricata como IDS para analizar tráfico de red e identificar actividad sospechosa según sus reglas, configuración y visibilidad. Se investigarán escaneos, tráfico malicioso, ataques web, intentos de explotación y tráfico relacionado con malware.

## Función prevista en el proyecto

- Centralizar eventos y detectar amenazas de sistemas y red.
- Generar y analizar alertas relevantes.
- Analizar simulaciones autorizadas de SQLi y DoS.
- Seleccionar eventos críticos para su notarización blockchain.

## Puntos para investigar

- Arquitectura de Wazuh e instalación de Server y Agents.
- Reglas y alertas de Wazuh.
- Funcionamiento de Suricata.
- Diferencias entre HIDS y NIDS.
- Análisis de logs y correlación de alertas.

## Fuentes y evidencias

Pendiente de añadir documentación oficial, artículos y capturas reales. No se presenta la detección como validada.
