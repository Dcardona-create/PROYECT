# Prometheus, Grafana y Nginx

Estado: borrador inicial conservado para revisión técnica y ampliación de fuentes.

[Volver al cuadro de investigaciones](../README.md)

## Prometheus

El borrador contempla recopilar métricas de sistemas, servicios y aplicaciones, consultar los datos y definir alertas para analizar el rendimiento.

## Grafana

Se prevé visualizar datos de Prometheus y otras fuentes mediante paneles. Los indicadores previstos incluyen CPU, memoria, red, estado de servicios y actividad de seguridad cuando existan integraciones adecuadas.

## Nginx

Se contempla como servidor web y posible proxy inverso. Sus funciones de gestión de acceso y balanceo dependen de la configuración que se diseñe; no se considera una protección automática.

## Función prevista en el proyecto

- Prometheus: recopilar métricas de máquinas virtuales y servicios.
- Grafana: mostrar el estado de la infraestructura en paneles.
- Nginx: publicar la aplicación y gestionar el acceso a los servicios.

## Puntos para investigar

- Métricas disponibles y sus integraciones.
- Creación de paneles en Grafana.
- Configuración y seguridad de Nginx.
- Integración de Prometheus con Grafana.

## Fuentes y evidencias

Pendiente de añadir documentación oficial, artículos y capturas reales.
