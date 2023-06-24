---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-22}
deciders: {Julián Moreno,Santiago Segura}
consulted: {Vilhai Maldonado, Nicolás Tibatá}
informed: {Felipe Palacios}
---
# Patrón de diseño Mediator para sistema de notificaciones

## Context and Problem Statement

Dentro de la factoría inteligente debe existir un sistema de notificaciones, que permita a  los operarios suscribirse para poder recibir las alertas. Estas alertas pueden generarse a partir de la información de los sensores y ordenes de trabajo.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Debe permitir la subscripción de los trabajadores. 
* Las notificaciones deben llegar en tiempo casi real. 


## Considered Options

* Patrón de diseño Mediator, [Observer](MADR_3_3_1.md)


<!-- This is an optional element. Feel free to remove. -->

## Pros and Cons of the Options

### Pros


Permite reducir el acoplamiento entre los componentes del sistema, 
Simplifica la comunicaicón entre los componentes, poniendo un agente central (mediador).
Es fácil agregar componentes al sistema.
Los componentes se vuelven más independientes, ya que no dependen de otros componentes, sino solo del mediador.


### Cons

Gran dependencia del mediador. Si esté queda mal implementado, puede fallar el sistema completo.
A medida que el sistema crece y se agregan componenetes, el mediador puede sobrecargarse. 
El tiempo de ejecución se ve directamente afectado por la eficacia del mediador. 
