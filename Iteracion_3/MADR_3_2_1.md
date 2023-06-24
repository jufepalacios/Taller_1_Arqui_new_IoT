---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-22}
deciders: {Julián Moreno,Santiago Segura}
consulted: {Vilhai Maldonado, Nicolás Tibatá}
informed: {Felipe Palacios}
---
# PostgreSQL: Componente base de datos para almacenamiento

## Context and Problem Statement

Dentro de la factoría inteligente debe existir un componente de almacenamiento de datos. Esta servirá para almacenar la infromación de los sensores, las órdenes de trabajo, el inventario. Con esta se podrán usar los datos en los tableros de control (dashboards) y modelos estádisticos. 

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Debe almacenar los datos generados por todos los sensores de la fábrica. 
* Debe almacenar las órdenes de trabajo generadas. 
* Debe ser tipo SQL (Requerimiento de cliente)
* Se podrá conectar con la herramienta de visualización escogida, para que sirva como fuente de alimentación de esta. 

## Considered Options

* PostgreSQL, [MySQL](MADR_3_2_2.md), [Oracle](MADR_3_2_3.md)


<!-- This is an optional element. Feel free to remove. -->

## Pros and Cons of the Options

### Pros

Soporte de consultas complejas y transacciones ACID.
Es de código abierto, por lo que no se incurren en gastos de licenciamiento. 
Extensibilidad con  diferente variedad de extensiones en diferentes lenguajes de programación.  


### Cons

Lento en inserciones y actualiaciones en bases de datos pequeñas. 
Para procesamiento de altos volumenes de datos, se necesita de recursos de hardware.
Al ser una herramienta de código abierto, no cuenta con soporte técnico oficial. Sin embargo, tiene una comunidad donde las dudas y problemas se pueden aclarar por medio de foros. 


