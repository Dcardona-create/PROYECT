# Investigación: DNS

Estado: documento de investigación teórica. No describe un despliegue realizado ni exige instalar Pi-hole.

[Volver al cuadro de investigaciones](../README.md) · [Volver a la portada](../../README.md)

## Índice de contenidos

1. [Fundamentos](#fundamentos)
2. [Resolución](#resolución)
3. [Registros](#registros)
4. [Roles de servidores](#roles-de-servidores)
5. [DNS en el proyecto](#dns-en-el-proyecto)
6. [Seguridad](#seguridad)
7. [Consulta DNS de ejemplo](#consulta-dns-de-ejemplo)
8. [Actividades](#actividades)
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

Este esquema explica roles; no representa una instalación realizada.

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

El pacto del equipo contempla Pi-hole como componente DNS. Su motor FTL integra funcionalidad basada en dnsmasq [2]. En esta investigación se estudia su posible función como servicio DNS local y reenviador hacia un upstream recursivo, sin presentar una configuración implantada.

Pi-hole no está instalado. La definición de direcciones IP, dominio interno, ubicación del servicio y configuración concreta queda fuera del alcance de este documento teórico.

No se presenta Pi-hole como un mecanismo que garantice privacidad completa o detección de todas las amenazas.

### Criterios para decidir el upstream

Como criterios teóricos para una posible elección se consideran:

- Disponibilidad y latencia desde la red del proyecto.
- Política de privacidad y tratamiento de consultas.
- Compatibilidad con DNSSEC, si se decide validar registros firmados.
- Posibilidad de definir un upstream secundario para tolerancia a fallos.
- Facilidad de monitorización desde Pi-hole y desde el SOC.

Estos criterios no implican que se haya seleccionado o configurado un upstream.

## Seguridad

### DNS Tunneling

El DNS tunneling es una técnica que utiliza consultas y respuestas DNS para transportar datos que no pertenecen normalmente al protocolo. Puede emplearse para establecer canales encubiertos, exfiltrar información o comunicarse con infraestructura maliciosa, aprovechando que el tráfico DNS suele estar permitido hacia el exterior.

No todo tráfico DNS anómalo implica un túnel. Para considerarlo indicativo, deben analizarse conjuntamente varios signos:

- Consultas a un mismo dominio con subdominios largos, aleatorios o con codificación inusual.
- Volumen elevado de consultas TXT, NULL u otros tipos poco habituales para navegación normal.
- Consultas repetitivas hacia el mismo dominio autoritativo desde un mismo cliente.
- TTL muy bajos combinados con un patrón constante de consultas.
- Tráfico DNS desproporcionado respecto al uso normal del equipo.

ACT1 se enlaza como material de aprendizaje relacionado con los canales encubiertos sobre DNS, no como evidencia obligatoria de un despliegue del proyecto.

### DNSSEC

DNSSEC aporta autenticación del origen e integridad de los datos DNS. No cifra las consultas ni proporciona confidencialidad [3]. No equivale a filtrado de dominios ni demuestra por sí solo que un dominio sea benigno.

### Controles de seguridad considerados

- Uso del DNS autorizado y política para consultas externas.
- Actualizaciones, permisos de administración y segmentación.
- Cobertura y límites del filtrado por listas.
- Análisis de consultas y correlación con eventos del SOC.
- Validación DNSSEC y límites de protección.
- Detección de patrones compatibles con DNS tunneling.

Estos controles se presentan como conceptos de investigación, no como configuraciones implantadas ni tareas prácticas exigidas.

## Consulta DNS de ejemplo

Los siguientes comandos son ejemplos de consulta, no resultados de pruebas realizadas ni actividades obligatorias.

El siguiente comando permite comprobar qué dirección responde un dominio y qué servidor DNS se utilizó:

```bash
nslookup example.com
```

Para consultar directamente a un resolvedor concreto:

```bash
nslookup example.com 1.1.1.1
```

## Actividades

| Actividad | Relación con la investigación | Acceso |
|---|---|---|
| ACT1 — DNS Tunneling | Seguridad y uso indebido del protocolo | [Ver actividad](https://github.com/Dcardona-create/Actividades-ASIXII/tree/main/ACT1-dns-tunneling) |
| ACT2 — Resolución DNS | Consultas y análisis de resolución | [Ver actividad](https://github.com/Dcardona-create/Actividades-ASIXII/tree/main/ACT2-dns-resolucion) |
| ACT3 — BIND9 | Contexto de instalación y configuración de un servicio DNS | [Ver actividad](https://github.com/Dcardona-create/Actividades-ASIXII/tree/main/ACT3-instalacion-bind9) |
| ACT4 — DNS secundario | Contexto de servidores y zonas | [Ver actividad](https://github.com/Dcardona-create/Actividades-ASIXII/tree/main/ACT4-dns-esclavo) |

Estas actividades se enlazan como material de aprendizaje. No constituyen evidencias obligatorias ni acreditan una instalación del proyecto. Las prácticas de BIND9 no implican sustituir la decisión de utilizar Pi-hole en el proyecto.

## Fuentes

1. RFC 1034 — Domain names: concepts and facilities: https://www.rfc-editor.org/info/rfc1034/
2. Pi-hole — DNS resolver / FTL: https://docs.pi-hole.net/ftldns/dns-resolver/
3. RFC 4033 — DNS Security Introduction and Requirements: https://www.rfc-editor.org/info/rfc4033/
4. RFC 2181 — Clarifications to the DNS Specification: https://www.rfc-editor.org/info/rfc2181/
5. Cloudflare — ¿Qué es el DNS?: https://www.cloudflare.com/es-es/learning/dns/what-is-dns/

Contexto del proyecto: Proyecto-pacto-de-socios.docx, aportado por el equipo. Las actividades enlazadas son material propio pendiente de análisis detallado.

### Registro de aportaciones

| Fecha | Integrante | Tema | Fuente | Conclusión y aplicación al proyecto |
|---|---|---|---|---|
| 2026-10-20 | Deivid Cardona | DNS Tunneling, criterios de upstream y consulta DNS | RFC 1034, RFC 4033, documentación de Pi-hole y Cloudflare | Se amplió el contenido teórico y se ajustó el alcance para no exigir instalación, capturas ni pruebas no solicitadas. |

[Volver al índice](#índice-de-contenidos) · [Volver a investigaciones](../README.md)
