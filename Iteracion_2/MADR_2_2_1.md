---
status: {accepted}
date: {2023-06-22}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Nicolas Tibatá, Vihlai Maldonado}
informed: {Juan Palacios}
---

# Clase "LecturaSensor" para la arquitectura de lectura

## Context and Problem Statement
La factoría 4.0 requiere que sus operarios estén permanentemente notificados del estado de las máquinas y de la línea de producción. Para ello se deben poder suscribir a diferentes eventos y notificaciones como actualizaciones en la producción, fallos de sensores o sobrecarga de producción. En caso de que se supere un umbral de intentos de conexión, se considerará que el dispositivo está fuera de servicio.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Lectura de datos de los sensores: Se requiere disponer de una BBDD escalable que permita almacenar los datos de los sensores y se puedan administar para el sistema de mensajería y notificación.
* Notificar actualizaciones de la producción: El sistema de notificación debe permitir notificar a tiempo y de manera precisa fallas en los sensores, sobrecarga de producción y actualizaciones.
* Notificar fallos de los sensores: Añadir al sistema de notificacion el fallo de sensores 
* Notificar sobrecarga en la producción: Añadir al sistema de notificacion la sobrecarga de producción
* Configurar umbral de un dispositivo: Configuracion de los umbrales de medición para poder notificar en el sistema de mensajería


## Considered Options
* Clase LecturaSensor

## Decision Outcome
Chosen option: "Clase LecturaSensor", porque es la solución más sencilla en cuanto a la lectura de datos dado por el procesamiento de los sensores.

### Consequences 
* Buena, ya que simplifica el procesamiento de datos y el servicio de mensajería.
* Buena, ya que es escalable y recibe todos los datos de manera estructurada con sus respectivos atributos.
* Buena, pues recibe directo del driver del sensor y es eficiente en el envio de informacion al broker de mensajería.
* Mala, pues es solo un mediador para recibir la informacion de los drivers y no permite una administración de los datos, solo es un canal de comunicación con el broker.

## Pros and Cons of the Options

## Clase "LecturaSensor"

La clase "LecturaSensor" recibirá los datos directos de los drivers y sus atributos relacionados como el tipo de sensor, su id, y el dato en si. Además de esto tendrá algunos metodos respectivos como la conexion del sensor, la lectura del sensor para recibir sus atributos y el envio de la lectura de los datos el broker de mensajería.

* Buena, simplifica el procesamiento de lectura de los datos a traves de los drivers, para ser enviados directamente al broker de mensajería.
* Buena, escalable ya que podra recibir de todo tipo de familia de sensores ya que serán identificados por su id.
