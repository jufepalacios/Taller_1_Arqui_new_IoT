---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-22}
deciders: {Julián Moreno,Santiago Segura}
consulted: {Vilhai Maldonado, Nicolás Tibatá}
informed: {Felipe Palacios}
---
# Patrón de diseño observer para sistema de notificaciones

## Context and Problem Statement

Dentro de la factoría inteligente debe existir un sistema de notificaciones, que permita a  los operarios suscribirse para poder recibir las alertas. Estas alertas pueden generarse a partir de la información de los sensores y ordenes de trabajo.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Debe permitir la subscripción de los trabajadores. 
* Las notificaciones deben llegar en tiempo casi real. 


## Considered Options

* Patrón de diseño Observer, [Mediator](MADR_3_3_2.md)


<!-- This is an optional element. Feel free to remove. -->

## Pros and Cons of the Options

### Pros


Permite desacoplar el sujeto y los observadores.
Se pueden agregar nuevos observadores sin necesidad de modificar el código existente. 
Cuando el sujeto cambia de estado, los observadores son notificados automáticamente. 

### Cons

Si hay muchos observadores registrados y el sujeto experimenta cambios constantes de estado, puede existir sobrecarga de notificaciones.
Si los observadores no están correctamente implementados. puede haber inconsistencias entre el estado del sujeto y el observador. 
Puede crearse un acomplamiento indirecto ya que los observadores deben tener conocimiento del sujeto y su interfaz para recibir las notificaciones. 
