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

* Apache Kafka
* Patrón publicador/suscriptor [Formato MADR](MADR_2_1_1.md)
* Apache ActiveMQ [Formato MADR](MADR_2_1_3.md)
* Patrón Broker [Formato MADR](MADR_2_1_4.md)




<!-- This is an optional element. Feel free to remove. -->
## Pros and Cons of the Options

### Apache Kafka

<!-- This is an optional element. Feel free to remove. -->
{example | description | pointer to more information | …}
Apache Kafka es un almacen de datos distribuido optimizado para la ingestay procesamiento de datos de flujo en tiempo real. Los datos en flujo son datos generados continuamente por miles de fuentes de datos, que normalmente envían los registros de datos de forma simultánea.

* Buena, es conocido por su alto rendimiento y baja latencia, lo que lo hace adecuado para casos de uso de transmisión de datos en tiempo real y procesamiento de eventos a gran escala.
* Buena, está diseñado para ofrecer una alta escalabilidad horizontal, lo que significa que puede manejar grandes volúmenes de datos y flujos de eventos distribuidos a través de múltiples nodos y particiones.
* Buena, proporciona una alta resiliencia gracias a su modelo de almacenamiento persistente y replicación de datos. Los mensajes se almacenan en disco y se replican en múltiples nodos, lo que garantiza una mayor tolerancia a fallos y recuperación ante situaciones adversas.
* Mala, Kafka almacena todos los mensajes de manera persistente en disco, lo que puede generar un mayor consumo de almacenamiento en comparación con otros sistemas de mensajería más efímeros. 

<!-- This is an optional element. Feel free to remove. -->
## More Information
[Mayor información sobre EDA](info/More_Information.md)
