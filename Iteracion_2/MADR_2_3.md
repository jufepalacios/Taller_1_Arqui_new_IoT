---
status: {proposed}
date: {2023-06-22}
deciders: {Nicolas Tibatá, Vihlai Maldonado}
consulted: {Julian Moreno, Santiago Segura}
informed: {Juan Palacios}
---

# Patrón Chain of responsibility para la arquitectura de mensajería

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
* Cadena de responsabilidad (chain of responsibility)

## Pros and Cons of the Options

## Patrón Chain of responsibility

Permite pasar peticiones a lo largo de una cadena de gestores. Al recibir una solicitud, cada gestor decide si procesarla o pasarla al siguiente gestor de cadena.

* Buena, procesamiento inidividual de cada evento, lo que permite personalizar la acción con cada mensaje recibido.
* Buena, complementación de acciones a los mensajes, donde permite indicar la tarea específica para cada mensaje.
* Mala, debido a eventos encadenados, los eventos solo deben ser notificados mas no procesados.
* Mala, los eventos no requieren ser procesados por diferentes handlers, por lo tanto es sobrecomplejizar la arquitectura.
* Mala, los eventos no requieren de peticiones para la generacion de notifiaciones, por lo tanto generaria un delay en el sistema.