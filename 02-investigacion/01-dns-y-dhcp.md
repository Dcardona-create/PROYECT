# DNS y DHCP

## DNS

El Sistema de Nombres de Dominio (DNS) traduce nombres de dominio, como `ejemplo.com`, en direcciones IP. Es un servicio esencial para acceder a páginas web y servicios de red sin memorizar direcciones IP.

En este proyecto, Pi-hole se utilizará como servicio DNS para mejorar la privacidad, bloquear dominios no deseados y controlar las consultas DNS de la red.

## Función en el proyecto

- Resolver nombres de dominio dentro de la red.
- Filtrar consultas hacia dominios maliciosos o publicitarios.
- Mejorar la privacidad y el control del tráfico DNS.
- Apoyar la configuración de los servicios alojados en la DMZ.

## DHCP

DHCP significa *Dynamic Host Configuration Protocol*. Es el protocolo que asigna automáticamente direcciones IP y otros parámetros de red a los dispositivos que se conectan.

En este proyecto, ISC-DHCP se utilizará para asignar direcciones IP a las máquinas virtuales y mantener una configuración de red ordenada.

## Función en el proyecto

- Asignar direcciones IP automáticamente.
- Entregar máscara de red, puerta de enlace y servidores DNS.
- Evitar errores manuales al configurar cada máquina.
- Mantener un control más sencillo de la red virtualizada.

## Puntos para investigar

- Tipos de registros DNS.
- Funcionamiento de una consulta DNS.
- Diferencias entre DHCP y DNS.
- Configuración básica de ISC-DHCP.
- Funcionamiento y ventajas de Pi-hole.

## Fuentes y referencias

- [Añadir fuente o documentación]
- [Añadir artículo o guía]
- [Añadir captura o evidencia]