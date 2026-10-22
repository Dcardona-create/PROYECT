# A2 — Wireframes y Mockups / Diseño

## Estado del apartado

Este documento recoge el avance del diseño de la interfaz de la aplicación web del proyecto **HOSTLOCK**. Se irá actualizando conforme se complete el prototipo en Figma.

**Herramienta de diseño:** Figma  
**Enlace al prototipo:** [Diseño wireframes y mockups — Figma Sites](https://www.figma.com/site/c4LcawrwLIGvA8g66faJZs/dise%C3%B1o-wireframes-y-mockups?node-id=0-1&p=f&t=kzL2FbanRVt3c7hY-0)  
**Última actualización:** 21/10/2026

## Objetivo

Definir la disposición de los elementos de la interfaz, la navegación entre pantallas y la información visible para cada perfil de usuario. Los wireframes muestran la estructura básica y los mockups incorporan la propuesta visual antes del desarrollo final.

## Mapa del sitio

```text
Inicio
├── Acceso / Login
├── Panel principal
│   ├── Estado de servicios
│   ├── Alertas
│   ├── Métricas
│   └── Evidencias
├── Gestión de incidentes
│   ├── Detalle de alerta
│   └── Evidencia asociada
└── Administración
    ├── Usuarios
    └── Configuración
```

## Perfiles de usuario

| Perfil | Descripción | Accesos previstos |
|---|---|---|
| Administrador | Gestiona usuarios, configuración y acceso general | Panel completo, administración, incidentes y evidencias |
| Analista SOC | Consulta alertas, eventos y evidencias | Panel, alertas, detalle de incidentes y evidencias |
| Usuario básico | Consulta el estado general del servicio | Panel resumido y estado de servicios |

## Wireframes y mockups

### 1. Inicio

**Wireframe:** *(añadir captura o enlace de Figma)*  
**Mockup:** *(añadir captura o enlace de Figma)*

**Elementos previstos:**

- Logotipo y nombre del proyecto.
- Menú principal.
- Botón de acceso.
- Breve descripción del servicio.
- Acceso al panel según el perfil.

**Navegación:**

- El botón **Acceder** lleva a la pantalla de login.
- El menú permite ir a las secciones disponibles según el perfil.

**Datos visibles:**

- Nombre del proyecto.
- Estado general del servicio.
- Opciones de navegación permitidas.

### 2. Login

**Wireframe:** *(añadir captura o enlace de Figma)*  
**Mockup:** *(añadir captura o enlace de Figma)*

**Elementos previstos:**

- Campo de usuario.
- Campo de contraseña.
- Botón de inicio de sesión.
- Mensaje de error en caso de credenciales incorrectas.

**Navegación:**

- Un inicio de sesión correcto lleva al panel principal.
- Un error mantiene al usuario en la pantalla de login y muestra un mensaje.

**Datos visibles:**

- Usuario introducido.
- Mensaje de validación o error.

### 3. Panel principal

**Wireframe:** *(añadir captura o enlace de Figma)*  
**Mockup:** *(añadir captura o enlace de Figma)*

**Elementos previstos:**

- Menú lateral o superior.
- Resumen del estado de los servicios.
- Acceso a alertas, métricas y evidencias.
- Botón de cierre de sesión.

**Navegación:**

- **Alertas** lleva a la gestión de incidentes.
- **Métricas** lleva a la vista de monitorización.
- **Evidencias** lleva al listado de registros conservados.

**Datos visibles:**

- Estado general de los servicios.
- Número de alertas activas.
- Últimas métricas disponibles.
- Accesos habilitados según el perfil.

### 4. Alertas e incidentes

**Wireframe:** *(añadir captura o enlace de Figma)*  
**Mockup:** *(añadir captura o enlace de Figma)*

**Elementos previstos:**

- Listado de alertas.
- Filtros por fecha, tipo o estado.
- Botón para abrir el detalle.
- Indicador del estado de cada alerta.

**Navegación:**

- Al seleccionar una alerta se accede a su detalle.
- Desde el detalle se puede consultar la evidencia asociada.

**Datos visibles:**

- Fecha y hora de la alerta.
- Tipo de evento.
- Estado de la alerta.
- Servicio o equipo relacionado.
- Acceso a la evidencia relacionada.

### 5. Detalle de alerta

**Wireframe:** *(añadir captura o enlace de Figma)*  
**Mockup:** *(añadir captura o enlace de Figma)*

**Elementos previstos:**

- Información principal de la alerta.
- Observaciones relacionadas.
- Botón para volver al listado.
- Acceso a la evidencia original.

**Navegación:**

- **Volver** regresa al listado de alertas.
- **Ver evidencia** abre la pantalla o registro asociado.

**Datos visibles:**

- Descripción del incidente.
- Fecha y hora.
- Origen o servicio afectado.
- Estado de análisis.
- Evidencia vinculada.

### 6. Evidencias

**Wireframe:** *(añadir captura o enlace de Figma)*  
**Mockup:** *(añadir captura o enlace de Figma)*

**Elementos previstos:**

- Listado de evidencias.
- Filtro por fecha o tipo de evento.
- Botón para consultar el detalle.
- Indicador de trazabilidad cuando corresponda.

**Navegación:**

- Al seleccionar una evidencia se accede a su detalle.
- El botón **Volver** regresa al panel o listado anterior.

**Datos visibles:**

- Identificador visible de la evidencia.
- Fecha y hora.
- Tipo de registro.
- Relación con la alerta o prueba.
- Estado de trazabilidad.

## Pruebas de navegabilidad

### Prueba 1 — Administrador

**Objetivo:** comprobar que el administrador puede acceder, consultar alertas y revisar evidencias.

**Pasos:**

1. Acceder a la pantalla de login.
2. Iniciar sesión con un usuario administrador.
3. Entrar en el panel principal.
4. Abrir la sección de alertas.
5. Seleccionar una alerta y acceder a su detalle.
6. Consultar la evidencia asociada.
7. Volver al panel principal.

**Resultado esperado:** todas las secciones son accesibles y la navegación vuelve correctamente al punto anterior.

### Prueba 2 — Analista SOC

**Objetivo:** comprobar que el analista puede consultar alertas y evidencias sin acceder a la administración.

**Pasos:**

1. Iniciar sesión como analista SOC.
2. Acceder al panel principal.
3. Abrir alertas.
4. Consultar el detalle de una alerta.
5. Acceder a la evidencia relacionada.
6. Comprobar que la sección de administración no está disponible.

**Resultado esperado:** el analista puede consultar la información operativa, pero no accede a las opciones de administración.

### Prueba 3 — Usuario básico

**Objetivo:** comprobar que el usuario básico solo visualiza la información permitida.

**Pasos:**

1. Iniciar sesión como usuario básico.
2. Acceder al panel resumido.
3. Consultar el estado de los servicios.
4. Intentar acceder a una sección no permitida.

**Resultado esperado:** el usuario ve únicamente el estado general y no puede acceder a alertas, evidencias ni administración.

## Registro de avances

| Fecha | Avance | Responsable |
|---|---|---|
| 21/10/2026 | Creación del documento inicial de wireframes y mockups | Deivid Cardona |
| 21/10/2026 | Añadido el enlace del prototipo de Figma Sites | Deivid Cardona |
