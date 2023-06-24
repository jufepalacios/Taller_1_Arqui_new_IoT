---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-22}
deciders: {Julián Moreno,Santiago Segura}
consulted: {Vilhai Maldonado, Nicolás Tibatá}
informed: {Felipe Palacios}
---
# MySQL: Componente base de datos para almacenamiento

## Context and Problem Statement

Dentro de la factoría inteligente debe existir un componente de almacenamiento de datos. Esta servirá para almacenar la infromación de los sensores, las órdenes de trabajo, el inventario. Con esta se podrán usar los datos en los tableros de control (dashboards) y modelos estádisticos. 

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Debe almacenar los datos generados por todos los sensores de la fábrica. 
* Debe almacenar las órdenes de trabajo generadas. 
* Debe ser tipo SQL (Requerimiento de cliente)
* Se podrá conectar con la herramienta de visualización escogida, para que sirva como fuente de alimentación de esta. 

## Considered Options

* MySQL, [PostgreSQL](MADR_3_2_1,md), [Oracle](MADR_3_2_3.md)


<!-- This is an optional element. Feel free to remove. -->

## Pros and Cons of the Options

### Pros

Es de código abierto, por lo que no se incurren en gastos de licenciamiento. 
Ofrece compatibilidad con la mayoría de las principales plataformas informáticas, como Linux, macOS, Microsoft Windows y Ubuntu.
MySQL brinda la posibilidad de que varios usuarios puedan acceder a los datos almacenados de forma simultánea  
Es veloz al realizar las operaciones, garantiza buen rendimiento de aplicaciones.
Ofrece un rendimiento sólido y escalable para manejar cargas de trabajo de diferente de tamaños. 
Puede gestionar grandes volúmenes de datos y soportar transacciones simultáneas. 

### Cons

Cuando se debe modificar la estructura de la base de datos puede haber un periodo (corto) de disponibilidad. 
La replicación se hace de forma asíncrona, por lo que puede haber cierta latencia entre la base de datos y su copia de seguridad. 
Su gestión de concurrencia está enfoqueado en bloqueo. Por lo que no es recomendada en casos donde hayan diferentes porceso de modificación de estructura de tabla, o eliminación de datos al mismo tiempo. 

