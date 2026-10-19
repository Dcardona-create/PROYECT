# Contexto del proyecto — SecChain SOC Solutions

[Portada](../README.md) · [Investigaciones y aplicativos](../02-investigacion/README.md) · [Equipo y seguimiento](../04-equipo/README.md)

## Presentación

SecChain SOC Solutions es un proyecto de infraestructura y ciberseguridad que propone construir un laboratorio virtualizado para proteger servicios web, observar su funcionamiento y analizar los incidentes que se produzcan durante pruebas controladas. Su propósito no es instalar herramientas de forma aislada, sino relacionar la configuración de la red, la supervisión de los sistemas y la conservación de evidencias dentro de un mismo escenario.

La propuesta une tres líneas de trabajo: separar los servicios expuestos de los recursos de administración, centralizar la detección y el análisis mediante un centro de operaciones de seguridad —SOC— y estudiar la notarización de eventos críticos en una red de pruebas de Ethereum. El resultado esperado es una demostración técnica documentada, no un servicio de seguridad en producción ni una garantía de protección absoluta.

## Necesidad que aborda

El escenario de trabajo es una infraestructura que publica una aplicación web y necesita conocer qué sucede tanto en sus servidores como en las comunicaciones de red. El proyecto parte de tres problemas que se investigarán en el laboratorio:

- Exposición de servicios: definir qué comunicaciones necesita la aplicación y cuáles deben restringirse, sin mezclar la administración con el acceso a los servicios publicados.
- Información dispersa: reunir registros de distintos equipos y relacionarlos con las observaciones del tráfico para analizar un incidente con contexto.
- Verificación posterior: conservar las evidencias de las pruebas y estudiar un mecanismo adicional para comprobar si los registros seleccionados han cambiado.

No se atribuyen estos problemas a una empresa real ni se presentan incidentes previos como hechos comprobados. Constituyen el escenario sobre el que se diseña y evaluará la solución.

## Objetivo y planteamiento

El objetivo es implementar y validar una infraestructura perimetral virtualizada en la que una prueba autorizada pueda seguirse desde el servicio afectado hasta la alerta y su evidencia asociada.

La separación de redes y el refuerzo de los sistemas forman la base preventiva. El SOC aporta la observación y el análisis de los eventos. La monitorización permite estudiar el comportamiento de los recursos. La notarización se incorpora como una capa adicional de trazabilidad para los eventos que se seleccionen, no como sustituto de los registros originales.

El valor del proyecto estará en demostrar la relación entre esas capas y explicar sus limitaciones, no únicamente en mostrar que los componentes están instalados.

## Organización de la solución

### Infraestructura y separación de redes

Proxmox VE será la base prevista para alojar las máquinas del laboratorio. La arquitectura distinguirá una red de gestión y una zona desmilitarizada —DMZ— destinada a los servicios publicados. El diseño deberá concretar qué equipos pertenecen a cada zona y qué comunicaciones se autorizan entre ellas.

DHCP y DNS proporcionarán direccionamiento y resolución de nombres. El planteamiento inicial contempla ISC-DHCP y Pi-hole; su configuración, adecuación y mantenimiento se revisarán antes de fijar el despliegue. El filtrado con iptables y las tareas de hardening deberán responder a las necesidades de comunicación documentadas, no a reglas añadidas sin justificación.

### Servicio web como escenario de observación

La aplicación web permitirá disponer de un servicio sobre el que estudiar configuración, exposición y detección. Se contempla Nginx para su publicación, HTML y CSS para la interfaz y MySQL para los datos. La tecnología de servidor que conectará la aplicación con la base de datos sigue pendiente de decisión; no se presupone una API ni una arquitectura de aplicación ya acordada.

El servicio web es parte del escenario de validación. Su desarrollo deberá coordinarse con la segmentación, el control de acceso y la generación de registros que después analizará el SOC.

### Detección y análisis de seguridad

El SOC combinará los eventos de los equipos con las observaciones del tráfico de red. Wazuh Server y Agents se contemplan para recopilar y analizar información de los sistemas, mientras que Suricata se utilizará para estudiar la detección basada en tráfico.

La investigación deberá establecer qué fuentes se recogen, dónde existe visibilidad y cómo se relaciona una alerta con la prueba que la originó. La existencia de una alerta no bastará por sí sola para dar por validada una detección: habrá que explicar qué se observó y qué quedó fuera de cobertura.

### Monitorización del funcionamiento

Prometheus y Grafana permitirán estudiar métricas y presentar el estado de los componentes mediante paneles. Esta línea se distingue del análisis de seguridad: describe el comportamiento de la infraestructura y aporta contexto para interpretar las pruebas, sin reemplazar los registros ni las alertas del SOC.

Las métricas, fuentes y paneles se elegirán según lo que deba comprobarse. Los scripts en Bash y Python servirán de apoyo a las tareas de automatización e integración que se definan.

### Trazabilidad de eventos críticos

Se prevé seleccionar determinados eventos del SOC y estudiar su notarización mediante un contrato inteligente en una red de pruebas de Ethereum. Web3 forma parte de las tecnologías previstas para esa integración.

Antes de implementarla se deberá definir qué se registra, cómo se vincula con la evidencia original y cómo se consulta después. El formato, los criterios de selección y el tratamiento de información sensible permanecen abiertos. No se presupone que se publicarán registros completos.

La notarización no se presentará como una prueba automática de que una alerta es verdadera ni de que la detección fue correcta. Su utilidad y sus límites se evaluarán en relación con las evidencias conservadas por el proyecto.

## Recorrido previsto de una prueba

1. Preparar el servicio y documentar su configuración y estado inicial.
2. Ejecutar una simulación autorizada de SQLi o DoS dentro del laboratorio.
3. Recoger los eventos de los sistemas y las observaciones de red disponibles.
4. Analizar las alertas y relacionarlas con la prueba y sus evidencias.
5. Seleccionar, si corresponde, un evento para el mecanismo de notarización definido.
6. Documentar el resultado, comprobar su trazabilidad y explicar las limitaciones encontradas.

Este recorrido describe lo que se pretende validar; no afirma que las pruebas o las integraciones ya se hayan realizado.

## Alcance y límites

| Incluido en el proyecto | Fuera del alcance de esta propuesta |
|---|---|
| Laboratorio virtualizado y redes separadas | Despliegue de un SOC comercial en producción |
| Servicio web, configuración y refuerzo de sistemas | Garantizar ausencia de vulnerabilidades |
| Recogida de eventos, análisis de alertas y métricas | Garantizar la detección de todos los ataques |
| Notarización experimental de eventos seleccionados | Sustituir las evidencias originales o prometer validez legal automática |
| Simulaciones controladas y documentación de resultados | Realizar pruebas sobre sistemas de terceros sin autorización |

## Desarrollo y criterios de validación

El trabajo seguirá una secuencia de dependencias: infraestructura y redes; servicio web y preparación del SOC; monitorización e integración de la trazabilidad; y pruebas finales. La configuración se revisará durante el proceso a partir de los resultados obtenidos.

Se proponen los siguientes criterios para organizar la evaluación, pendientes de concretar con el diseño técnico:

- Segmentación: documentar y comprobar comunicaciones permitidas y restringidas.
- Funcionamiento: demostrar que los servicios previstos operan dentro del escenario definido.
- Observabilidad: identificar las fuentes de eventos y métricas realmente disponibles.
- Detección: contrastar las alertas con las simulaciones y describir las ausencias de detección o falsas alertas que se observen.
- Trazabilidad: relacionar la prueba, la evidencia original y el registro de notarización cuando exista.
- Documentación: conservar configuraciones, capturas y resultados suficientes para entender y repetir las comprobaciones en el laboratorio.

## Estado y documentación relacionada

El repositorio se encuentra en fase de investigación y organización documental. Las direcciones de red, versiones, reglas, tecnología de servidor de la aplicación y mecanismo exacto de notarización deben concretarse durante el desarrollo. No se presentan resultados experimentales que todavía no se hayan obtenido.

Este contexto desarrolla el planteamiento recogido en Proyecto-pacto-de-socios.docx y en la documentación actual del repositorio. Los detalles técnicos, fuentes y evidencias se mantienen en [Investigaciones y aplicativos](../02-investigacion/README.md); la autoría, responsabilidades y seguimiento se consultan en [Equipo](../04-equipo/README.md).
