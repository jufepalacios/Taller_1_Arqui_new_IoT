---
status: {proposed}
date: {2023-06-20}
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
* Clase “LecturaSensor” 
* Hub and Spoke [Formato MADR](MADR_2_2_2.md)
* DAO [Formato MADR](MADR_2_2_3.md)

## Pros and Cons of the Options

## Clase "LecturaSensor"

La clase "LecturaSensor" recibirá los datos directos de los drivers y sus atributos relacionados como el tipo de sensor, su id, y el dato en si. Además de esto tendrá algunos metodos respectivos como la conexion del sensor, la lectura del sensor para recibir sus atributos y el envio de la lectura de los datos el broker de mensajería.

* Buena, simplifica el procesamiento de lectura de los datos a traves de los drivers, para ser enviados directamente al broker de mensajería.
* Buena, escalable ya que podra recibir de todo tipo de familia de sensores ya que serán identificados por su id.
