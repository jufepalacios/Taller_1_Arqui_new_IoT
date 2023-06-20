---
status: {proposed}
date: {2023-06-17}
deciders: {Nicolas Tibatá, Vihlai Maldonado}
consulted: {Julian Moreno, Santiago Segura}
informed: {Juan Palacios}
---

# {Sekección de patrones de arquitectura para mensajería}

## Context and Problem Statement
La factoría 4.0 requiere que sus operarios estén permanentemente notificados del estado de las máquinas y de la línea de producción. Para ello se deben poder suscribir a diferentes eventos y notificaciones como actuailizaciones en la produccción, fallos de sensores o sobrecarga de producción. En caso de que se supere un umbral de intentos de conexión, se considerará que el dispositivo está fuera de servicio.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Almacenamiento - almacenar la información recopilada por los sensores, el inventario y las ordenes de trabajo.

## Considered Options

* Patrón publicador/suscriptor (Publish Suscriber)
* Broker de mensajes
* Cadena de responsabilidad (chain of responsibility)


* … <!-- numbers of options can vary -->

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

### Patrón publicador/suscriptor 


* Buena, porque permite desacomplamiento, esta solución permite el desacople de los subsistemas que necesitan comunicarse.
* Buena, dado que ofrece escalabilidad. Permite una mayor escalabilidad y mejora la capacidad de respuesta del remitente.
* Buena, debido a que ofrece confiabilidad, la mensajería asíncronica permite que las aplicaciones controlen las intermitencias.
* Mala, ya que puede incurrir en duplicación de mensajes, la implementación debe considerar la deduplicación de los mensajes que puede ocurrir debido a errores en el publicador.
* Mala, ya que se debe incluir la expiración de los mensajes. Esto para evitar incrementar el tamaño de la cola de mensajes, se debe incluir un tiempo de expiración y asegurar que el mensaje fue procesado para evitar pérdida de información.
* Neutral, orden de los mensajes. La implementación necesita asegurar que el orden del envío de los mensajes de cada sensor es con tiempo incremental, para asegurar que la información visualizada y consumida por los suscriptores sea la correcta.

### BROKER DE MENSAJES	

* Buena, Flexibilidad, mantenibilidad y adaptibilidad.
* Mala, dependencia del intermediario ya que se agrega un elemento crítico en la comunicación, el intermediario.
* Buena, escalabilidad ya que hay posibilidad de distribución.
* Mala, Escalabilidad limitada: A pesar de poder lograr escalar, esta tiene la limitante de los recursos del intermediarios.
* Buena, interoperabilidad entre brokers.	
			
	
## More Information

{You might want to provide additional evidence/confidence for the decision outcome here and/or
 document the team agreement on the decision and/or
 define when/how this decision the decision should be realized and if/when it should be re-visited.
Links to other decisions and resources might appear here as well.}
