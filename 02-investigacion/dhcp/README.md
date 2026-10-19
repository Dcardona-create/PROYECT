# Investigación: DHCP

Estado: borrador inicial; pendiente de revisión técnica y fuentes.

[Volver al cuadro de investigaciones](../README.md)

## Contexto

Este documento separa DHCP del resumen anterior de DNS y DHCP. La investigación de DNS se conserva en [su página propia](../dns/README.md).

## DHCP

DHCP significa Dynamic Host Configuration Protocol. El borrador del proyecto contempla ISC-DHCP para asignar direcciones IP y parámetros de red a las máquinas virtuales.

## Función prevista en el proyecto

- Asignar direcciones IP automáticamente.
- Entregar máscara de red, puerta de enlace y servidores DNS.
- Reducir errores de configuración manual.
- Facilitar la administración de la red virtualizada.

## Puntos para investigar

- Funcionamiento y configuración de ISC-DHCP.
- Diferencias y relación entre DHCP y DNS.
- Concesiones, reservas y distribución de parámetros de red.
- Compatibilidad, mantenimiento y adecuación de la herramienta antes del despliegue.

Las versiones, direcciones y configuraciones están pendientes de definir. No se documenta un despliegue ya realizado.

## Fuentes y evidencias

Pendiente de añadir documentación oficial, artículos y capturas reales.
