---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-22}
deciders: {Santiago Segura, Felipe Palacios}
consulted: {Vilhai Maldonado, Julián Moreno}
informed: {Nicolás Tibatá}
---
# Componente base de datos para almacenamiento

## Context and Problem Statement

Dentro de la factoría inteligente debe existir un componente de almacenamiento de datos. Esta servirá para almacenar la infromación de los sensores, las órdenes de trabajo, el inventario. Con esta se podrán usar los datos en los tableros de control (dashboards) y modelos estádisticos. 

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Debe almacenar los datos generados por todos los sensores de la fábrica. 
* Debe almacenar las órdenes de trabajo generadas. 
* Debe ser tipo SQL (Requerimiento de cliente)
* Se podrá conectar con la herramienta de visualización escogida, para que sirva como fuente de alimentación de esta. 

## Considered Options

* Oracle


<!-- This is an optional element. Feel free to remove. -->

## Pros and Cons of the Options

### Pros


Ofrece una mayor seguridad de los datos. 
Tiene una optimización eficiente de las consultas complejas. 
Permite una escalabilidad  que  es alta en comparación con softwares del  mercado. 

### Cons

No es cñodigo abierto, por lo que toca pagar  por tener la licencia de este. 
Dependencia del proovedor (Oracle)
Existen limitaciones d portabilidad y de instañación dependiendo del hardware. 

