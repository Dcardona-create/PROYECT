# Investigaciones y aplicativos del proyecto

Documentación técnica de SecChain SOC Solutions. DNS es la investigación activa; los demás temas son borradores. Las herramientas indicadas son tecnologías previstas, no despliegues completados.

## Cuadro de investigaciones

| Investigación | Área | Contenido | Estado | Acceso |
|---|---|---|---|---|
| DNS | Servicios de red | Fundamentos, resolución, registros, Pi-hole, seguridad y prácticas | En desarrollo | [Leer DNS](./dns/README.md) |
| DHCP | Servicios de red | Direccionamiento automático y parámetros de red | Borrador inicial | [Leer DHCP](./dhcp/README.md) |
| SOC, Wazuh y Suricata | Ciberseguridad | Eventos, detección y alertas | Borrador inicial | [Leer investigación](./soc-wazuh-suricata/README.md) |
| Prometheus, Grafana y Nginx | Monitorización y servicios web | Métricas, paneles y publicación web | Borrador inicial | [Leer investigación](./monitorizacion-y-web/README.md) |
| Hardening, Proxmox e iptables | Infraestructura y seguridad | Virtualización, refuerzo y filtrado | Borrador inicial | [Leer investigación](./hardening-e-infraestructura/README.md) |
| Blockchain y contratos inteligentes | Trazabilidad | Notarización de eventos críticos | Borrador inicial | [Leer investigación](./blockchain/README.md) |
| Seguridad web y ataques | Validación de seguridad | SQLi y DoS en laboratorio autorizado | Borrador inicial | [Leer investigación](./seguridad-web/README.md) |
| Fuentes y referencias | Documentación | Registro de fuentes y aportaciones | Pendiente de completar | [Leer referencias](./referencias/README.md) |

## Cuadro de aplicativos y tecnologías

Las herramientas, lenguajes y entornos se reúnen aquí para evitar catálogos duplicados. Los enlaces abren su explicación técnica o el contexto de uso en el proyecto; no un listado de archivos.

| Aplicativo o tecnología | Qué es | Función prevista | Contexto y explicación |
|---|---|---|---|
| Proxmox VE | Plataforma de virtualización | Administrar máquinas virtuales y contenedores | [Leer](./hardening-e-infraestructura/README.md) |
| ISC-DHCP | Servicio de configuración automática de red | Distribuir IP, máscara, puerta de enlace y DNS; adecuación pendiente de revisar | [Leer](./dhcp/README.md) |
| Pi-hole | Componente DNS con filtrado por listas | Resolver nombres y aplicar la política de filtrado definida | [Leer](./dns/README.md#dns-en-el-proyecto) |
| iptables | Herramienta de filtrado en Linux | Controlar comunicaciones entre redes y servicios | [Leer](./hardening-e-infraestructura/README.md) |
| Nginx | Servidor web y posible proxy inverso | Publicar la aplicación y gestionar su acceso | [Leer](./monitorizacion-y-web/README.md) |
| MySQL | Sistema de base de datos | Almacenar datos; modelo e integración pendientes | [Contexto de uso](./mysql/README.md) |
| HTML | Tecnología de estructura web | Organizar el contenido de la interfaz | [Contexto de uso](./html/README.md) |
| CSS | Tecnología de presentación web | Definir el aspecto visual de la interfaz | [Contexto de uso](./css/README.md) |
| Wazuh Server y Agents | Componentes de análisis y recopilación de eventos | Centralizar logs, monitorizar integridad y generar alertas | [Leer](./soc-wazuh-suricata/README.md) |
| Suricata IDS | Detector de intrusiones en red | Analizar tráfico según reglas y visibilidad | [Leer](./soc-wazuh-suricata/README.md) |
| Prometheus | Herramienta de métricas | Recopilar y consultar métricas de máquinas y servicios | [Leer](./monitorizacion-y-web/README.md) |
| Grafana | Plataforma de paneles | Visualizar datos de las fuentes conectadas | [Leer](./monitorizacion-y-web/README.md) |
| Python | Lenguaje previsto para automatización | Desarrollar tareas e integraciones pendientes de concretar | [Contexto de uso](./python/README.md) |
| Bash | Lenguaje de scripts | Automatizar tareas de administración pendientes de concretar | [Contexto de uso](./bash/README.md) |
| Web3 | Tecnología de interacción con blockchain | Conectar los componentes con el contrato inteligente | [Contexto de uso](./web3/README.md) |
| Ethereum Testnet | Entorno de pruebas de Ethereum | Probar la notarización sin operar en la red principal con fondos reales | [Leer](./blockchain/README.md) |
| Smart Contract | Programa ejecutado en blockchain | Gestionar pruebas de eventos seleccionados; formato pendiente | [Leer](./blockchain/README.md) |

## Recursos de apoyo al hardening

Su aplicación concreta sigue pendiente de definición. No se presentan como componentes ya desplegados.

| Recurso | Contexto previsto | Acceso |
|---|---|---|
| PowerShell | Conocimiento del equipo para administración y automatización; alcance pendiente | Sin investigación específica todavía |
| Lynis | Estudio de auditorías de seguridad de sistemas | [Leer](./hardening-e-infraestructura/README.md) |
| Docker Bench | Estudio de seguridad en contenedores | [Leer](./hardening-e-infraestructura/README.md) |
| CIS e INCIBE | Guías y recursos para reforzar sistemas; no son aplicativos | [Leer](./hardening-e-infraestructura/README.md) |

Las versiones, requisitos, integraciones, testnet, mecanismo de notarización y fuentes oficiales verificadas se completarán durante la investigación. El componente de servidor que conectará la aplicación con MySQL sigue pendiente de decisión. Un enlace de contexto no equivale a una investigación individual terminada.

[Contexto del proyecto](../01-contexto/README.md) · [Volver a la portada](../README.md)
