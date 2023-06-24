---
status: {proposed}
date: {2023-06-22}
deciders: {Nicolas Tibatá, Vihlai Maldonado}
consulted: {Julian Moreno, Santiago Segura}
informed: {Juan Palacios}
---

# Patrón Broker de mensajes para la arquitectura de mensajería

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

* Broker de mensajes

## Pros and Cons of the Options

### Broker de mensajes
Patrón de diseño arquitectónico que se utiliza para facilitar la comunicación entre diferentes componentes o sistemas distribuidos. En este patrón, un componente centralizado conocido como "broker" actúa como intermediario entre los productores de mensajes y los consumidores. Los productores envían mensajes al broker, que luego los enruta y distribuye a los consumidores interesados en esos mensajes. El broker maneja las tareas de encolamiento, enrutamiento y entrega de mensajes, lo que permite una comunicación desacoplada entre los diferentes componentes.

* Buena, flexibilidad, mantenibilidad y adaptibilidad.
* Mala, dependencia del intermediario ya que se agrega un elemento crítico en la comunicación, el intermediario.
* Buena, escalabilidad ya que hay posibilidad de distribución.
* Mala, Escalabilidad limitada ya que a pesar de poder escalar, esta tiene la limitante de los recursos del intermediarios.
* Buena, interoperabilidad entre brokers.