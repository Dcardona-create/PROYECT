# A2 — Diseño de la interfaz de HOSTLOCK

## Datos de la actividad

| Campo | Información |
|---|---|
| Alumno | Deivid Cardona |
| Módulo | M0379 / Proyecto |
| Ciclo | ASIX 2.º |
| Herramienta | Figma |
| Actualización | 22/10/2026 |

## Objetivo

Diseñar cinco pantallas de HOSTLOCK y explicar sus funcionalidades, navegación e información visible por perfil. Figma se utiliza como guía visual. Los comportamientos descritos corresponden al diseño previsto de la web, no a funciones implementadas.

## Archivos de diseño

- [Figma Design](https://www.figma.com/design/lSyFDomQELzVXsKalm0OQp/)
- [Figma Sites original](https://www.figma.com/site/c4LcawrwLIGvA8g66faJZs/)

## Alcance y funcionalidades

La entrega comprende Inicio, Servicios, Acceso, Panel general y Monitorización. Permite representar la presentación pública, el inicio de sesión, la consulta según perfil y el cierre de sesión. No incluye pantallas independientes de administración, alertas, incidentes o evidencias.

## Mapa del sitio

```text
Inicio
├── Servicios — público
└── Acceso
    ├── Administrador / Analista SOC
    │   └── Panel general
    │       ├── Monitorización
    │       └── Cerrar sesión → Acceso
    └── Usuario básico
        └── Panel general resumido
            └── Cerrar sesión → Acceso
```

## Perfiles

| Perfil | Información visible y acceso previsto |
|---|---|
| Administrador | Vista completa del Panel general y Monitorización detallada. |
| Analista SOC | Los mismos datos de consulta, sin funciones de administración. |
| Usuario básico | Estado general de los servicios, sin métricas detalladas de CPU, RAM, disco o red ni acceso a Monitorización detallada. |

Administrador y analista comparten la vista de consulta, identificando su rol. La vista resumida es una variante del Panel general, no una sexta pantalla.

## Boceto inicial

## Pantallas, wireframes y mockups

### 1. Inicio

Su función prevista es presentar HOSTLOCK y permitir acceder a Servicios y Acceso.

#### Wireframe

#### Mockup

### 2. Servicios

Pantalla pública con la misma información para todos los visitantes. Presenta tres tarjetas informativas, sin acciones ni pantallas adicionales:

| Tarjeta | Texto visible |
|---|---|
| Infraestructura | Redes y servicios organizados en un entorno virtualizado. |
| Ciberseguridad | Supervisión de sistemas y análisis de eventos del laboratorio. |
| Evidencias | Estudio de la trazabilidad y la integridad de registros seleccionados. |

La cabecera muestra HOSTLOCK y el lema «Infraestructura y ciberseguridad en un mismo entorno». La presentación dice: «Un laboratorio académico para supervisar servicios, analizar eventos de seguridad y estudiar la integridad de las evidencias». El pie identifica el proyecto académico de ASIX.

| Elemento | Funcionamiento previsto |
|---|---|
| Inicio | Regresar a Inicio. |
| Servicios | Identificar la sección actual. |
| Acceso | Abrir el formulario de inicio de sesión. |
| Menú | Mostrar u ocultar las opciones de navegación. |

El diseño acordado prescinde de «Explorar el proyecto». Existen wireframes de escritorio, tablet y móvil; las copias del mockup de escritorio se destinarán a adaptar esas versiones.

#### Wireframe

#### Mockup

### 3. Acceso

La composición representa un formulario. El funcionamiento previsto consiste en introducir usuario y contraseña y pulsar Entrar para abrir el panel correspondiente al perfil. La contraseña se mostrará oculta. Las credenciales incorrectas mantendrán la pantalla de acceso con un aviso de error.

Esta descripción no implica autenticación real implementada.

#### Wireframe

#### Mockup

### 4. Panel general

El diseño muestra HOSTLOCK, navegación lateral y gráficos ilustrativos de Tráfico de red, Alertas por día y Uso de recursos. Los gráficos no son resultados reales del laboratorio. El resumen de alertas no implica una pantalla de gestión de alertas.

Administrador y analista consultan la vista completa y pueden abrir Monitorización. El usuario básico consulta solo el estado general de los servicios, sin gráficos detallados ni acceso a Monitorización. Cerrar sesión conduce a Acceso.

#### Wireframe

#### Mockup

#### Vista resumida del usuario básico

### 5. Monitorización

El diseño de escritorio incorpora colores verdes, cabecera HOSTLOCK, siete etiquetas superiores y tres bloques visuales:

| Bloque | Contenido representado |
|---|---|
| Estado del servidor | Imagen ilustrativa del estado del equipo. |
| Tráfico de red | Imagen ilustrativa de actividad de red. |
| Rendimiento del servicio | Imagen ilustrativa del rendimiento. |

La barra superior muestra Panel general, Monitorización, CPU, Memoria RAM, Disco, Red y Cerrar sesión. CPU, Memoria RAM, Disco y Red son indicadores informativos: no son botones y no abren pantallas ni tienen acciones.

La franja inferior identifica «Equipo: Servidor web · Última actualización: — · Datos de demostración». El pie muestra «HOSTLOCK · Proyecto académico ASIX». Las cifras de las imágenes son ilustrativas, no mediciones reales.

| Elemento | Funcionamiento previsto |
|---|---|
| Panel general | Regresar al panel. |
| Monitorización | Identificar la pantalla actual. |
| CPU, Memoria RAM, Disco y Red | Identificar métricas de consulta sin interacción. |
| Cerrar sesión | Regresar a Acceso. |

Esta pantalla se reserva a administrador y analista SOC. El usuario básico no dispone de acceso a la monitorización detallada.

#### Wireframe

#### Mockup

## Pruebas de navegación previstas

Son comprobaciones planificadas de la navegación y los perfiles; no resultados de pruebas ejecutadas. Las explicaciones describen el funcionamiento esperado, sin afirmar que las conexiones estén configuradas en Figma.

| Escenario | Pasos | Resultado esperado |
|---|---|---|
| Visitante | Inicio → Servicios → Acceso. | Lee los tres bloques públicos y llega al formulario sin ver información interna. |
| Administrador | Acceso → Panel completo → Monitorización → Panel → Cerrar sesión. | Consulta los datos detallados y regresa a Acceso. |
| Analista SOC | Acceso → Panel completo → Monitorización → Cerrar sesión. | Consulta los datos operativos sin funciones de administración. |
| Usuario básico | Acceso → Panel resumido → Cerrar sesión. | Ve únicamente el estado general; no encuentra métricas detalladas ni acceso a Monitorización. |
| Error de acceso | Introducir credenciales de ejemplo incorrectas y pulsar Entrar. | Permanece en Acceso con un mensaje de error. |

## Registro de avances

| Fecha | Avance | Responsable |
|---|---|---|
| 21/10/2026 | Documento inicial y enlace a Figma Sites. | Deivid Cardona |
| 22/10/2026 | Cinco pantallas acordadas, revisión de Servicios y Monitorización y definición de perfiles e indicadores informativos. | Deivid Cardona |
