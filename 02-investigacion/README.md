# Investigaciones y aplicativos del proyecto

Punto de entrada a la documentación técnica de SecChain SOC Solutions. Consulta las investigaciones o selecciona un aplicativo para conocer qué es y para qué se prevé utilizarlo.

DNS es la investigación activa. Las demás investigaciones son borradores; las herramientas son tecnologías previstas, no despliegues completados.

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

Cada enlace abre una sección del documento correspondiente, no un listado de archivos. Se incluyen herramientas, lenguajes y entornos; no todos son aplicaciones instalables.

| Aplicativo o tecnología | Qué es | Para qué se prevé utilizar en el proyecto | Contexto y explicación |
|---|---|---|---|
| Proxmox VE | Plataforma de virtualización | Crear y administrar máquinas virtuales y contenedores de la infraestructura | [Qué es y función](./hardening-e-infraestructura/README.md#proxmox-ve) |
| ISC-DHCP | Servicio de asignación automática de parámetros de red | Distribuir direcciones IP, máscara, puerta de enlace y DNS; pendiente de revisar su adecuación | [Qué es y función](./dhcp/README.md#dhcp) |
| Pi-hole | Componente DNS con filtrado por listas | Gestionar consultas y nombres locales y aplicar la política de filtrado que se defina | [Contexto DNS y decisiones](./dns/README.md#dns-en-el-proyecto) |
| iptables | Herramienta de filtrado de tráfico en Linux | Definir reglas de comunicación entre redes y servicios | [Qué es y función](./hardening-e-infraestructura/README.md#iptables) |
| Nginx | Servidor web y posible proxy inverso | Publicar la aplicación y gestionar el acceso según la configuración | [Qué es y función](./monitorizacion-y-web/README.md#nginx) |
| MySQL | Sistema de base de datos | Almacenar los datos de la aplicación; modelo e integración pendientes | [Contexto de la aplicación](../03-aplicativos/README.md#hosting-y-aplicación) |
| HTML | Tecnología para estructurar la interfaz web | Organizar el contenido de las páginas de la aplicación | [Contexto web](../03-aplicativos/README.md#hosting-y-aplicación) |
| CSS | Tecnología para la presentación de la interfaz web | Definir el aspecto visual de las páginas | [Contexto web](../03-aplicativos/README.md#hosting-y-aplicación) |
| Wazuh Server y Agents | Componentes de recopilación y análisis de eventos de seguridad | Centralizar logs, monitorizar integridad y generar alertas | [Qué son y función](./soc-wazuh-suricata/README.md#wazuh) |
| Suricata IDS | Sistema de detección de intrusiones en red | Analizar tráfico y generar alertas según reglas y visibilidad | [Qué es y función](./soc-wazuh-suricata/README.md#suricata) |
| Prometheus | Herramienta de recopilación y consulta de métricas | Monitorizar máquinas y servicios mediante las integraciones configuradas | [Qué es y función](./monitorizacion-y-web/README.md#prometheus) |
| Grafana | Plataforma de visualización mediante paneles | Consultar el estado de la infraestructura a partir de las fuentes conectadas | [Qué es y función](./monitorizacion-y-web/README.md#grafana) |
| Python | Lenguaje previsto para automatización e integración | Desarrollar tareas de conexión entre componentes, pendientes de concretar | [Contexto de automatización](../03-aplicativos/README.md#monitorización-y-blockchain) |
| Bash | Lenguaje de scripts previsto para automatización | Automatizar tareas de administración, pendientes de concretar | [Contexto de automatización](../03-aplicativos/README.md#monitorización-y-blockchain) |
| Web3 | Tecnología de interacción con blockchain | Conectar la integración del proyecto con el contrato inteligente | [Contexto de integración](../03-aplicativos/README.md#monitorización-y-blockchain) |
| Ethereum Testnet | Entorno de pruebas de Ethereum | Probar el contrato y la notarización sin utilizar la red principal con fondos reales | [Contexto blockchain](./blockchain/README.md#blockchain) |
| Smart Contract | Programa para gestionar registros o pruebas en blockchain | Notarizar eventos seleccionados; formato y datos pendientes de definir | [Qué es y función](./blockchain/README.md#contratos-inteligentes) |

## Recursos de apoyo al hardening

Estos recursos se mencionan como apoyo o conocimientos del equipo; su utilización concreta todavía debe definirse.

| Recurso | Contexto previsto | Acceso |
|---|---|---|
| PowerShell | Apoyo a tareas de administración y automatización; alcance pendiente | [Contexto del equipo](../03-aplicativos/README.md#herramientas-de-apoyo-al-hardening) |
| Lynis | Estudio de auditorías de seguridad de sistemas | [Contexto de hardening](./hardening-e-infraestructura/README.md#hardening) |
| Docker Bench | Estudio de seguridad en contenedores | [Contexto de hardening](./hardening-e-infraestructura/README.md#hardening) |
| CIS e INCIBE | Guías y recursos de referencia para reforzar sistemas; no son aplicativos | [Contexto de hardening](./hardening-e-infraestructura/README.md#hardening) |

Las versiones, requisitos, integraciones y fuentes oficiales verificadas siguen pendientes de completar. Los enlaces reutilizan el contexto ya documentado; no implican que cada herramienta tenga todavía una investigación individual terminada.

[Ver catálogo de aplicativos](../03-aplicativos/README.md) · [Volver a la portada](../README.md)
