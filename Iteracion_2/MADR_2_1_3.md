---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-20}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Nicolas Tibatá, Vihlai Maldonado}
informed: {Juan Palacios}
---
# Selección del Broker para el sistema de mensajería

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

* Apache ActiveMQ
* Patrón publicador/suscriptor [Formato MADR](MADR_2_1_1.md)
* Apache Kafka [Formato MADR](MADR_2_1_2.md)
* Patrón Broker [Formato MADR](MADR_2_1_4.md)

## Pros and Cons of the Options

### ActiveMQ
ActiveMQ es una plataforma de mensajería de software de código abierto que implementa el protocolo Java Message Service (JMS). Proporciona una infraestructura robusta y escalable para el intercambio de mensajes entre aplicaciones distribuidas. ActiveMQ se basa en un modelo de publicador/suscriptor (pub/sub) y permite a las aplicaciones productoras enviar mensajes a colas o tópicos, y a las aplicaciones consumidoras recibir y procesar esos mensajes de manera asíncrona.

