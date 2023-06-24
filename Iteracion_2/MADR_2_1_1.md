---
status: {proposed}
date: {2023-06-20}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Nicolas Tibatá, Vihlai Maldonado}
informed: {Juan Palacios}
---

# Patrón publicador/suscriptor para la arquitectura de mensajería

## Context and Problem Statement
La factoría 4.0 requiere que sus operarios estén permanentemente notificados del estado de las máquinas y de la línea de producción. Para ello se deben poder suscribir a diferentes eventos y notificaciones como actualizaciones en la producción, fallos de sensores o sobrecarga de producción. En caso de que se supere un umbral de intentos de conexión, se considerará que el dispositivo está fuera de servicio.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Lectura de datos de los sensores: Se requiere disponer de una BBDD escalable que permita almacenar los datos de los sensores y se puedan administrar para el sistema de mensajería y notificación.
* Acceso al sistema de notificación por mensajería interna: 	El sistema de notificación permite notificar de alguna noticia relacionada a los sensores como actualizaciones de la producción, fallos en los sensores o sobrecarga en la producción.
* Notificar actualizaciones de la producción: El sistema de notificación debe permitir notificar a tiempo y de manera precisa fallas en los sensores, sobrecarga de producción y actualizaciones.
* Notificar fallos de los sensores: Añadir al sistema de notificación el fallo de sensores 
* Notificar sobrecarga en la producción:	Añadir al sistema de notificación la sobrecarga de producción
* Configurar umbral de un dispositivo: Configuración de los umbrales de medición para poder notificar en el sistema de mensajería


## Considered Options

* Patrón publicador/suscriptor (Publish Suscriber)
* Apache Kafka [Formato MADR](MADR_2_1_2.md)
* Apache ActiveMQ [Formato MADR](MADR_2_1_3.md)
* Patrón Broker [Formato MADR](MADR_2_1_4.md)


<!-- This is an optional element. Feel free to remove. -->
## Pros and Cons of the Options

### Patrón publicador/suscriptor 

Un objeto llamado publicador mantiene una lista de suscriptores u observadores interesados en ser notificados de cambios o eventos ocurridos en el sujeto. Cuando se produce un evento relevante, el sujeto notifica automáticamente a todos los suscriptores registrados, quienes pueden realizar acciones o procesar la información recibida. Este patrón permite una comunicación eficiente y desacoplada entre componentes, ya que el sujeto no necesita tener conocimiento directo de los suscriptores y los suscriptores no están acoplados directamente al sujeto, lo que facilita la extensibilidad y la reutilización del código.
La mensajería asíncrona es una forma eficaz de desacoplar a los remitentes de los consumidores y evitar el bloqueo del remitente para esperar una respuesta.


* Buena, porque permite desacoplamiento, esta solución permite el desacople de los subsistemas que necesitan comunicarse.
* Buena, dado que ofrece escalabilidad. Permite una mayor escalabilidad y mejora la capacidad de respuesta del remitente.
* Buena, debido a que ofrece confiabilidad, la mensajería asincrónica permite que las aplicaciones controlen las intermitencias.
* Mala, ya que puede incurrir en duplicación de mensajes, la implementación debe considerar la deduplicación de los mensajes que puede ocurrir debido a errores en el publicador.
* Neutral, orden de los mensajes. La implementación necesita asegurar que el orden del envío de los mensajes de cada sensor está dada conforme se van generando de acuerdo a su `timestamp`, de manera incremental, para asegurar que la información visualizada y consumida por los suscriptores esté en el orden correcto.
