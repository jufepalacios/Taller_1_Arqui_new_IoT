---
status: {proposed}
date: {2023-06-20}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Nicolas Tibatá, Vihlai Maldonado}
informed: {Juan Palacios}
---

# Patrón DAO para la arquitectura de lectura

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
* Hub and Spoke [Formato MADR](MADR_2_2_2.md)
* DAO

## Pros and Cons of the Options

## Patrón DAO

El patrón DAO es utilizado para proporcionar una capa de abstracción entre la aplicación y la fuente de datos, lo que permite un acceso transparente y eficiente a los datos almacenados en una base de datos. Dejando un código más claro y estructurado.

* Buena, Reusabilidad del código, lo que permite que cambiando la capa de persistencia sea necesario únicamente cambiar el DAO
* Buena, separación de responsabilidades, ayuda a separar la lógica de acceso a datos de la lógica de negocio
* Mala, puede incurrir en sobrecarga de rendimiento debido a la abstracción y las capas adicionales involucradas en la recuperación de datos
* Mala, se requiere de un conocimiento previo al patron debido a que se debe aplicar correctamente para su correcto funcionamiento.
