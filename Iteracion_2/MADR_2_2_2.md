---
status: {proposed}
date: {2023-06-20}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Nicolas Tibatá, Vihlai Maldonado}
informed: {Juan Palacios}
---

# Patrón Hub and Spoke para la arquitectura de lectura

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
* Clase “LecturaSensor” [Formato MADR](MADR_2_2_1.md)
* Hub and Spoke
* DAO [Formato MADR](MADR_2_2_3.md)

## Pros and Cons of the Options

## Patrón Hub and Spoke

El patrón Hub and Spoke se utiliza como comunicador de datos. En este patrón, se establece un nodo central llamado "concentrador" que actúa como punto central de conexión para otros nodos periféricos llamados "satélites".

* Buena, adaptación al cambio, donde se pueden añadir spokes al sistema sin necesidad de mucha complejizacion.
* Buena, se puede reusar, donde el sistema base puede ser replicado para concentrar datos de otro tipo de sensores.
* Mala, dependencia del concentrador, donde si el concentrador falla todos los nodos perifecos no podran comunicarse.
* Mala, escalabilidad limitada: Donde entre más nodos perifericos haya, hay más riesgo de un cuello de botella en el hub.
* Mala, no hay una manera adicional a que los nodos perifericos se puedan comnicar, sólo mediante el concentrador.
