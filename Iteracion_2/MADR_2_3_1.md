---
status: {proposed}
date: {2023-06-20}
deciders: {Nicolas Tibatá, Vihlai Maldonado}
consulted: {Julian Moreno, Santiago Segura}
informed: {Juan Palacios}
---

# Patrón Chain of Responsibility para la arquitectura de procesamiento

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
* Chain of Responsibility
* Circuit Breaker [Formato MADR](MADR_2_3_2.md)

## Pros and Cons of the Options

## Patrón Chain of Responsibility

El patrón Chain of Responsibility es un patrón de diseño comportamental que permite establecer la línea que deben llevar los mensajes para que los objetos realicen la tarea indicada. Es decir que cada «handler» procesa la información o la petición y la pasa al siguiente manejador. 

* Buena, procesamiento inidividual de cada evento, lo que permite personalizar la accion con cada lectura recibida, esto a través de handlers.
* Buena, complementacion de acciones a las peticiones.
* Buena, el procesamiento de los datos del lector deben ser enviados del sensor 1 al sensor 2 y del sensor 2 al sensor 3. Por lo tanto si cumple con el requerimiento funcional.
* Mala, procesamiento encadenado, por lo tanto la lectura solo se da cuando los sensores están en perfecto funcionamiento.
