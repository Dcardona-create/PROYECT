# Investigación: DNS

Estado: en desarrollo. Documento de investigación, no memoria de un despliegue completado.

[Volver al cuadro de investigaciones](../README.md) · [Volver a la portada](../../README.md)

## Índice de contenidos

1. [Fundamentos](#fundamentos)
2. [Resolución](#resolución)
3. [Registros](#registros)
4. [Roles de servidores](#roles-de-servidores)
5. [DNS en el proyecto](#dns-en-el-proyecto)
6. [Seguridad](#seguridad)
7. [Actividades](#actividades)
8. [Evidencias](#evidencias)
9. [Fuentes](#fuentes)

## Fundamentos

DNS es un sistema de nombres jerárquico y distribuido. Permite consultar información asociada a nombres de dominio; traducir nombres a direcciones IP es uno de sus usos, pero también publica información de correo, delegación y otros servicios [1].

Un dominio pertenece al espacio de nombres. Una zona es una parte de ese espacio administrada como unidad y puede delegar subdominios. Un servidor autoritativo publica los datos de las zonas que sirve [1].

## Resolución

Para una consulta que no puede resolverse con información local o almacenada:

1. El cliente consulta al servicio DNS configurado.
2. Si ese servicio reenvía consultas, las entrega a su servidor upstream; no tiene por qué consultar él mismo a la raíz.
3. El resolvedor recursivo busca la respuesta. Cuando necesita recorrer la jerarquía, consulta servidores raíz, recibe una referencia al TLD y obtiene después la referencia a los servidores autoritativos del dominio.
4. El servidor autoritativo devuelve los datos disponibles o la respuesta correspondiente.
5. El resolvedor responde al cliente y conserva en caché los datos según su TTL.

El TTL limita cuánto tiempo pueden reutilizarse los datos en caché. Una consulta puede resolverse sin recorrer toda la jerarquía si ya hay información válida almacenada [1].

### Esquema conceptual

```text
Cliente → DNS configurado / Pi-hole → upstream recursivo
                                      ↓ si no hay caché suficiente
                                  raíz → TLD → autoritativo
```

Este esquema explica roles; no representa todavía la topología definitiva del laboratorio.

## Registros

| Registro | Función |
|---|---|
| A | Dirección IPv4 |
| AAAA | Dirección IPv6 |
| CNAME | Alias de otro nombre |
| MX | Servidores de correo y su preferencia |
| NS | Servidores autoritativos de una zona o delegación |
| PTR | Referencia a otro nombre; habitual en resolución inversa |
| TXT | Datos de texto utilizados por diferentes mecanismos |
| SOA | Datos administrativos de la zona, incluido el número de serie |

La especificación base describe los registros y la organización del sistema; los tipos y extensiones posteriores requieren sus referencias específicas al ampliar esta sección [1].

## Roles de servidores

| Rol | Responsabilidad |
|---|---|
| Recursivo | Buscar una respuesta para el cliente utilizando caché y consultas a otros servidores |
| Autoritativo | Publicar los datos de las zonas que sirve |
| Reenviador | Entregar consultas a otro servicio DNS |
| Servicio local | Resolver nombres internos o aplicar políticas locales; no es un rol de protocolo excluyente de los anteriores |

## DNS en el proyecto

El pacto del equipo contempla Pi-hole como componente DNS. Su motor FTL integra funcionalidad basada en dnsmasq [2]. La arquitectura concreta debe documentar cómo se resolverán los nombres internos y a qué upstream se enviarán las consultas externas.

### Decisiones pendientes

- Ubicación de Pi-hole y equipos que podrán consultarlo.
- Direcciones IP, dominio interno y registros locales: pendientes, no inventados.
- Resolver upstream elegido y justificación.
- Listas y política de filtrado, excepciones y mantenimiento.
- Retención y acceso a los registros de consultas.
- Integración con la monitorización y el SOC: pendiente de diseñar y validar.

No se presenta Pi-hole como un mecanismo que garantice privacidad completa o detección de todas las amenazas.

## Seguridad

### DNS Tunneling

La actividad ACT1 se utilizará para contextualizar los canales encubiertos sobre DNS. Sus resultados, capturas y conclusiones deben revisarse antes de incorporarlos como evidencia. Queda pendiente añadir una referencia técnica específica y desarrollar los indicadores de detección.

### DNSSEC

DNSSEC aporta autenticación del origen e integridad de los datos DNS. No cifra las consultas ni proporciona confidencialidad [3]. No equivale a filtrado de dominios ni demuestra por sí solo que un dominio sea benigno.

### Controles que se investigarán

- Uso del DNS autorizado y política para consultas externas.
- Actualizaciones, permisos de administración y segmentación.
- Cobertura y límites del filtrado por listas.
- Análisis de consultas y correlación con eventos del SOC.
- Validación DNSSEC y límites de protección.

Estas medidas son líneas de investigación, no configuraciones ya implantadas.

## Actividades

| Actividad | Relación con la investigación | Acceso |
|---|---|---|
| ACT1 — DNS Tunneling | Seguridad y uso indebido del protocolo | [Ver actividad](https://github.com/Dcardona-create/Actividades-ASIXII/tree/main/ACT1-dns-tunneling) |
| ACT2 — Resolución DNS | Consultas y análisis de resolución | [Ver actividad](https://github.com/Dcardona-create/Actividades-ASIXII/tree/main/ACT2-dns-resolucion) |
| ACT3 — BIND9 | Contexto de instalación y configuración de un servicio DNS | [Ver actividad](https://github.com/Dcardona-create/Actividades-ASIXII/tree/main/ACT3-instalacion-bind9) |
| ACT4 — DNS secundario | Contexto de servidores y zonas | [Ver actividad](https://github.com/Dcardona-create/Actividades-ASIXII/tree/main/ACT4-dns-esclavo) |

Las prácticas de BIND9 son material de aprendizaje: no implican sustituir la decisión de utilizar Pi-hole en el proyecto.

## Evidencias

| Evidencia prevista | Qué deberá mostrar | Estado |
|---|---|---|
| Diagrama de resolución | Cliente, Pi-hole, upstream y jerarquía DNS | Pendiente |
| Consulta DNS real | Pregunta, respuesta, servidor consultado y TTL | Pendiente |
| Panel de Pi-hole | Consulta permitida o bloqueada y explicación del resultado | Pendiente |
| Evidencia de ACT1 | Observación de la práctica y limitaciones | Pendiente de revisar |

No se insertan enlaces a imágenes inexistentes. Las capturas reales se incorporarán tras revisarlas y ocultar los datos sensibles.

## Fuentes

1. RFC 1034 — Domain names: concepts and facilities: https://www.rfc-editor.org/info/rfc1034/
2. Pi-hole — DNS resolver / FTL: https://docs.pi-hole.net/ftldns/dns-resolver/
3. RFC 4033 — DNS Security Introduction and Requirements: https://www.rfc-editor.org/info/rfc4033/

Contexto del proyecto: Proyecto-pacto-de-socios.docx, aportado por el equipo. Las actividades enlazadas son material propio pendiente de análisis detallado.

### Registro de aportaciones

| Fecha | Integrante | Tema | Fuente | Conclusión y aplicación al proyecto |
|---|---|---|---|---|
| Pendiente | Pendiente | Pendiente | Pendiente | Pendiente |

[Volver al índice](#índice-de-contenidos) · [Volver a investigaciones](../README.md)
