---
status: {proposed}
date: {2023-06-22}
deciders: {Nicolas Tibatá, Vihlai Maldonado}
consulted: {Julian Moreno, Santiago Segura}
informed: {Juan Palacios}
---

# Patrón publicador/suscriptor para la arquitectura de mensajería

## Context and Problem Statement
La factoría 4.0 requiere que sus operarios estén permanentemente notificados del estado de las máquinas y de la línea de producción. Para ello se deben poder suscribir a diferentes eventos y notificaciones como actuailizaciones en la produccción, fallos de sensores o sobrecarga de producción. En caso de que se supere un umbral de intentos de conexión, se considerará que el dispositivo está fuera de servicio.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Lectura de datos de los sensores: Se requiere disponer  de una BBDD escalable que permita almacenar los datos de los sensores y se puedan administar para el sistema de mensajería y notificación.
* Acceso al sistema de notificacion por mensajeria interna: 	El sistema de notificación permite notificar de alguna noticia relacionada a los sensores como actualizaciones de la producción, fallos en los sensores o sobrecarga en la producción.
* Notificar actualizaciones de la producción: El sistema de notificación debe permitir notificar a tiempo y de manera precisa fallas en los sensores, sobrecarga de producción y actualizaciones.
* Notificar fallos de los sensores: Añadir al sistema de notificacion el fallo de sensores 
* Notificar sobrecarga en la producción:	Añadir al sistema de notificacion la sobrecarga de producción
* Configurar umbral de un dispositivo: Configuracion de los umbrales de medición para poder notificar en el sistema de mensajería


## Considered Options

* Patrón publicador/suscriptor (Publish Suscriber)



## Decision Outcome

Chosen option: "Patrón pub/sub", porque resuelve los requerimientos funcionales ya que permite a los operadores suscribirse a diferentes eventos y notificaciones, asimismo, tiene una mejor escalabilidad

<!-- This is an optional element. Feel free to remove. -->
### Consequences
* Buena, ya que permite el desacoplamiento entre los productores de mensajes (publicadores) y los consumidores de mensajes (suscriptores).

* Buena, ya que es adecuado para sistemas distribuidos y escalables.

* Buena, ya que es fácil agregar nuevos suscriptores sin afectar a los publicadores existentes.

* Mala, ya que puede incurrir en duplicación de mensajes.

<!-- This is an optional element. Feel free to remove. -->
## Pros and Cons of the Options

### Patrón publicador/suscriptor 

Un objeto llamado publicador mantiene una lista de suscriptores u observadores interesados en ser notificados de cambios o eventos ocurridos en el sujeto. Cuando se produce un evento relevante, el sujeto notifica automáticamente a todos los suscriptores registrados, quienes pueden realizar acciones o procesar la información recibida. Este patrón permite una comunicación eficiente y desacoplada entre componentes, ya que el sujeto no necesita tener conocimiento directo de los suscriptores y los suscriptores no están acoplados directamente al sujeto, lo que facilita la extensibilidad y la reutilización del código.
La mensajería asíncrona es una forma eficaz de desacoplar a los remitentes de los consumidores y evitar el bloqueo del remitente para esperar una respuesta.


* Buena, porque permite desacomplamiento, esta solución permite el desacople de los subsistemas que necesitan comunicarse.
* Buena, dado que ofrece escalabilidad. Permite una mayor escalabilidad y mejora la capacidad de respuesta del remitente.
* Buena, debido a que ofrece confiabilidad, la mensajería asíncronica permite que las aplicaciones controlen las intermitencias.
* Mala, ya que puede incurrir en duplicación de mensajes, la implementación debe considerar la deduplicación de los mensajes que puede ocurrir debido a errores en el publicador.
* Neutral, orden de los mensajes. La implementación necesita asegurar que el orden del envío de los mensajes de cada sensor esta dada conforme se van generando de acuerdo a su `timestamp`, de manera incremental, para asegurar que la información visualizada y consumida por los suscriptores esté en el orden correcto.


## More Information

{You might want to provide additional evidence/confidence for the decision outcome here and/or
 document the team agreement on the decision and/or
 define when/how this decision the decision should be realized and if/when it should be re-visited.
Links to other decisions and resources might appear here as well.}
