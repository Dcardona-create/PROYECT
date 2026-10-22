# A2 — Diseño de la interfaz de HOSTLOCK

## Datos y estado

- Alumno: Deivid Cardona.
- Módulo: M0379 / Proyecto.
- Ciclo: ASIX 2.º.
- Herramienta: Figma.
- Estado: diseño en desarrollo; no se presentan pruebas como ejecutadas.
- Actualización: 22/10/2026.

## Enlaces de trabajo

- [Archivo de Design revisable](https://www.figma.com/design/lSyFDomQELzVXsKalm0OQp/)
- [Archivo original de Sites](https://www.figma.com/site/c4LcawrwLIGvA8g66faJZs/)

La revisión documental se basa en la copia de Design y las capturas compartidas. Los cambios posteriores en Sites deben copiarse a Design para que ambos archivos coincidan.

## Objetivo y alcance acordado

Definir las funciones, estructura, información visible y navegación de la aplicación mediante bocetos, wireframes y mockups.

La entrega se centra en cinco pantallas: Inicio, Servicios, Acceso, Panel general y Monitorización. Alertas detalladas, gestión de incidentes, evidencias, gestión de usuarios y configuración quedan como ampliaciones futuras, no como pantallas realizadas ni como recorridos exigidos en esta versión.

No es necesario implementar el backend para representar estos recorridos en el prototipo. Los datos ilustrativos no son resultados del laboratorio.

## Mapa del sitio previsto

```text
Inicio
├── Servicios — público
└── Acceso
    └── Panel general — según perfil
        ├── Monitorización — según perfil
        └── Cerrar sesión → Acceso
```

El mapa describe los destinos previstos. Sus conexiones están pendientes de validación en el prototipo.

## Perfiles confirmados

| Perfil | Alcance de esta entrega |
|---|---|
| Administrador | Panel general y monitorización; las funciones de administración avanzada quedan fuera del prototipo mínimo. |
| Analista SOC | Consulta operativa del panel y monitorización; información exacta pendiente de concretar por pantalla. |
| Usuario básico | Consulta resumida del estado general; información restringida y diferencias visuales pendientes de concretar. |

No se consideran implementados los permisos. Debe definirse la información exacta de cada perfil antes de cerrar el diseño.

## Boceto inicial

El alumno confirma que dispone de un boceto en papel. Pendiente de incorporar su fotografía o digitalización.

## Pantallas y avance real

### 1. Inicio

Existe una sección denominada Inicio en Design. Pendiente de revisar sus elementos internos, identificar su wireframe y mockup e incorporar sus capturas.

Función prevista: presentar HOSTLOCK y permitir acceder a Servicios o Acceso.

Pendiente: concretar textos visibles, botones y destinos de esta pantalla sin confundirla con Servicios.

### 2. Servicios

#### Contenido revisado

La pantalla presenta HOSTLOCK mediante tres bloques informativos:

| Bloque | Texto visible |
|---|---|
| Infraestructura | Redes y servicios organizados en un entorno virtualizado. |
| Ciberseguridad | Supervisión de sistemas y análisis de eventos del laboratorio. |
| Evidencias | Estudio de la trazabilidad y la integridad de registros seleccionados. |

Incluye el lema «Infraestructura y ciberseguridad en un mismo entorno», una presentación del laboratorio académico y el pie «HOSTLOCK · Proyecto académico ASIX».

#### Acceso y navegación

Servicios será público y mostrará el mismo contenido informativo a todos los visitantes, sin datos privados del laboratorio.

- Inicio: volver a la pantalla inicial.
- Servicios: señalar la pantalla actual.
- Acceso: abrir el formulario de inicio de sesión.
- Menú: mostrar u ocultar las opciones de navegación.
- Las tres tarjetas son informativas y no abren pantallas adicionales.

Se acuerda retirar «Explorar el proyecto» para simplificar. Su retirada del diseño todavía no se ha verificado.

#### Estado y pendientes

- Revisados wireframes Desktop, Tablet y Móvil.
- Revisados tres mockups con tamaño de escritorio; dos se adaptarán a tablet y móvil.
- Pendiente separar las opciones de menú en elementos independientes y asignar destinos.
- En la copia de Design revisada, el mockup no contiene interacciones configuradas. Una tarjeta del wireframe tiene una acción de clic sin destino; debe retirarse al ser informativa.
- Pendiente revisar legibilidad, incorporar capturas y comprobar navegación.

### 3. Acceso

Existe el apartado de wireframe y UI; las capturas compartidas muestran la composición visual del formulario.

Elementos previstos: título «Iniciar sesión», campo Usuario, campo Contraseña con caracteres ocultos, botón Entrar y mensaje de error.

Recorrido previsto: acceso correcto simulado → Panel general; error simulado → permanecer en Acceso; regreso → Inicio.

Pendiente revisar las capas internas, completar etiquetas, representar el error y comprobar conexiones. El prototipo no demuestra autenticación real.

### 4. Panel general

Existe el apartado de wireframe y UI. La captura compartida muestra cabecera HOSTLOCK, menú lateral, título del panel, acceso a Mi perfil y gráficos de tráfico de red, alertas por día y uso de recursos.

Pendiente:

- Ajustar el menú al alcance mínimo; no dejar enlaces aparentes a pantallas futuras.
- Completar indicadores superiores.
- Definir datos, unidades, periodos y equipo representado.
- Sustituir o explicar etiquetas genéricas de las imágenes de gráficos.
- Concretar qué ve cada perfil.
- Mantener Mi perfil solo si se resuelve dentro de las cinco pantallas, sin añadir otra pantalla obligatoria.

Los gráficos actuales son ilustrativos. Mostrar un resumen de alertas no implica disponer de una pantalla de gestión de alertas.

### 5. Monitorización

Existen secciones de wireframe y UI en Design. El alumno confirma que está pendiente completar colores y contenido.

Antes de cerrar este apartado se definirán: nombre del equipo o servicio, métricas visibles, unidades, periodo, última actualización y diferencias por perfil.

No se fijan cifras ni se afirma que la monitorización esté implementada. Pendiente revisar su contenido interno cuando se complete y comprobar el regreso al Panel general.

## Pruebas de navegación previstas

Estas pruebas son propuestas, no resultados obtenidos. Se ajustarán a los datos y permisos definitivos.

| Perfil o escenario | Recorrido | Resultado esperado |
|---|---|---|
| Visitante | Inicio → Servicios → Acceso | Puede leer los tres bloques y llegar al formulario sin iniciar sesión. |
| Administrador | Acceso → Panel general → Monitorización → Panel → Cerrar sesión | Recorre las cinco pantallas aplicables y vuelve a Acceso sin enlaces sin destino. |
| Analista SOC | Acceso → Panel → Monitorización → Panel | Consulta la información operativa acordada, sin opciones de administración fuera del alcance. |
| Usuario básico | Acceso → Panel resumido → vista permitida de Monitorización → Cerrar sesión | Solo ve información resumida; pendiente concretar y representar esa vista. |
| Error de acceso | Acceso → Entrar con credenciales de ejemplo incorrectas | Se representa un mensaje de error y no se avanza al panel. |

Las conexiones deben simularse en Figma. No se presentan estas pruebas como comprobación de seguridad de una aplicación real.

## Lista de comprobación de A2

- [x] Herramienta online y enlaces identificados.
- [x] Alcance de cinco pantallas acordado.
- [x] Tres perfiles confirmados.
- [x] Servicios público y tarjetas informativas acordados.
- [x] Apartados de wireframe y UI localizados para Servicios, Acceso, Panel y Monitorización.
- [ ] Incorporar el boceto en papel.
- [ ] Revisar Inicio y el contenido interno de las pantallas restantes.
- [ ] Completar colores y contenido de Monitorización.
- [ ] Terminar las adaptaciones de tablet y móvil previstas.
- [ ] Definir la información exacta visible por pantalla y perfil.
- [ ] Anotar funciones y destinos de los elementos de navegación.
- [ ] Configurar y revisar las conexiones del prototipo.
- [ ] Incorporar capturas identificadas de wireframes y mockups.
- [ ] Comprobar el acceso del profesor al informe y al prototipo.

## Registro de avances

| Fecha | Avance | Responsable |
|---|---|---|
| 21/10/2026 | Documento inicial y enlace a Figma Sites. | Deivid Cardona |
| 22/10/2026 | Copia en Design para revisión; revisión de Servicios y acuerdo de cinco pantallas, tres perfiles y adaptaciones pendientes. | Deivid Cardona |
