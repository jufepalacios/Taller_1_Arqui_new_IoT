---
# These are optional elements. Feel free to remove any of them.
status: "Pending"
date: {2023-06-21}
deciders: {list everyone involved in the decision}
consulted: {list everyone whose opinions are sought (typically subject-matter experts); and with whom there is a two-way communication}
informed: {list everyone who is kept up-to-date on progress; and with whom there is a one-way communication}
---
# {Selección del Broker}

## Context and Problem Statement
La factoría 4.0 requiere que sus operarios estén permanentemente notificados del estado de las máquinas y de la línea de producción. Para ello se deben poder suscribir a diferentes eventos y notificaciones como actuailizaciones en la produccción, fallos de sensores o sobrecarga de producción. En caso de que se supere un umbral de intentos de conexión, se considerará que el dispositivo está fuera de servicio.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* {decision driver 1, e.g., a force, facing concern, …}
* {decision driver 2, e.g., a force, facing concern, …}
* … <!-- numbers of drivers can vary -->

## Considered Options

* ActiveMQ

## Decision Outcome

Chosen option: "{title of option 1}", because
{justification. e.g., only option, which meets k.o. criterion decision driver | which resolves force {force} | … | comes out best (see below)}.

<!-- This is an optional element. Feel free to remove. -->
### Consequences

* Good, because {positive consequence, e.g., improvement of one or more desired qualities, …}
* Bad, because {negative consequence, e.g., compromising one or more desired qualities, …}
* … <!-- numbers of consequences can vary -->

<!-- This is an optional element. Feel free to remove. -->
### Confirmation

{Describe how the implementation of/compliance with the ADR is confirmed. E.g., by a review or an ArchUnit test.
 Although we classify this element as optional, it is included in most ADRs.}

<!-- This is an optional element. Feel free to remove. -->
## Pros and Cons of the Options

### ActiveMQ

ActiveMQ es una plataforma de mensajería de software de código abierto que implementa el protocolo Java Message Service (JMS). Proporciona una infraestructura robusta y escalable para el intercambio de mensajes entre aplicaciones distribuidas. ActiveMQ se basa en un modelo de publicador/suscriptor (pub/sub) y permite a las aplicaciones productoras enviar mensajes a colas o tópicos, y a las aplicaciones consumidoras recibir y procesar esos mensajes de manera asíncrona.


* Buena, ofrece un rendimiento sólido en casos de uso de mensajería, aunque puede tener una latencia ligeramente más alta en comparación con Kafka en escenarios de alto rendimiento.
* Buena, ofrece opciones de escalabilidad, pero puede tener limitaciones en comparación con Kafka cuando se trata de manejar grandes volúmenes de datos y cargas de trabajo distribuidas.
* Buena, ofrece cierto nivel de resiliencia con características como almacenamiento persistente, clustering y replicación, pero puede requerir configuraciones adicionales para lograr niveles de resiliencia similares a los de Kafka.
* Mala, ActiveMQ admite el escalado horizontal mediante el uso de clústeres pero puede tener algunas limitaciones en cuanto a su capacidad para manejar grandes volúmenes de mensajes y cargas de trabajo distribuidas en comparación con soluciones como Apache Kafka.
* Mala,  en comparación con otras soluciones de mensajería como Apache Kafka, ActiveMQ puede tener un rendimiento relativamente más bajo, especialmente en escenarios de alto volumen y alta concurrencia. Puede experimentar latencia más alta en situaciones de carga intensa.

<!-- This is an optional element. Feel free to remove. -->
## More Information

{You might want to provide additional evidence/confidence for the decision outcome here and/or
 document the team agreement on the decision and/or
 define when/how this decision the decision should be realized and if/when it should be re-visited.
Links to other decisions and resources might appear here as well.}
