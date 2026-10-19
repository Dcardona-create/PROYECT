# Seguridad web y ataques

Estado: borrador inicial conservado para revisión técnica y ampliación de fuentes.

[Volver al cuadro de investigaciones](../README.md)

## Seguridad web

La propuesta busca proteger la disponibilidad, integridad y confidencialidad de una aplicación alojada con Nginx y conectada a MySQL. El componente de servidor de la aplicación está pendiente de definir.

## Inyección SQL

Se investigará cómo las entradas no confiables pueden alterar consultas cuando la aplicación las construye de forma insegura, y las medidas de prevención correspondientes.

## Denegación de servicio

Se investigarán incidentes DoS y DDoS y su impacto en la disponibilidad. Las simulaciones se limitarán al laboratorio propio y expresamente autorizado.

## Función prevista en el proyecto

- Comprobar la detección por Wazuh y Suricata mediante pruebas autorizadas.
- Analizar las alertas obtenidas y sus limitaciones.
- Seleccionar incidentes críticos para notarización.
- Validar la trazabilidad del sistema sin presentar resultados no obtenidos.

## Puntos para investigar

- Vulnerabilidades web y funcionamiento de SQLi.
- Prevención de inyección SQL.
- Tipos de DoS y DDoS.
- Buenas prácticas en Nginx y MySQL.

## Fuentes y evidencias

Pendiente de añadir documentación oficial, artículos y capturas reales.
