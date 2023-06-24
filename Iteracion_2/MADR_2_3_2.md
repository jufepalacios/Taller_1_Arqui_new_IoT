---
status: {proposed}
date: {2023-06-20}
deciders: {Nicolas Tibatá, Vihlai Maldonado}
consulted: {Julian Moreno, Santiago Segura}
informed: {Juan Palacios}
---

# Patrón Circuit Breaker para la arquitectura de procesamiento

## Context and Problem Statement
La factoría 4.0 requiere que sus operarios estén permanentemente notificados del estado de las máquinas y de la línea de producción. Para ello se deben poder suscribir a diferentes eventos y notificaciones como actuailizaciones en la produccción, fallos de sensores o sobrecarga de producción. En caso de que se supere un umbral de intentos de conexión, se considerará que el dispositivo está fuera de servicio.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Notificar actualizaciones de la producción: El sistema de notificación debe permitir notificar a tiempo y de manera precisa fallas en los sensores, sobrecarga de producción y actualizaciones.
* Notificar fallos de los sensores: Añadir al sistema de notificacion el fallo de sensores 
* Notificar sobrecarga en la producción: Añadir al sistema de notificacion la sobrecarga de producción
* Configurar umbral de un dispositivo: Configuracion de los umbrales de medición para poder notificar en el sistema de mensajería
* Suspender intentos de conexión de dispositivo


## Considered Options
* Chain of Responsibility [Formato MADR](MADR_2_3_1.md)
* Circuit Breaker

## Pros and Cons of the Options

## Patrón Circuit Breaker

El patrón Circuit Breaker es un mecanismo utilizado en sistemas distribuidos para mejorar la resiliencia. Actúa como un interruptor que monitorea las llamadas a servicios externos y evita llamadas adicionales si el servicio falla o está sobrecargado. Es perfecto para temas donde se requieran baja latencia en envīo de mensajes. 

* Buena, define la entrada de peticiones en diferentes servicios, sin embargo no son tantos servicios como para utilizar esta opción.
* Buena, evita la propagación de errores al sistema, cambiando su estatus a cerrado.
* Mala, las peticiones no van a ser tantas como para bloquear el sistema, no se ajusta a nuestro requerimiento funcional.
* Mala, a pesar de que tiene un buen sistema de solución para grandes cantidades de peticiones, falta la parte de encadenar los datos de los sensores.
