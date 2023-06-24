---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-22}
deciders: {Julián Moreno,Santiago Segura}
consulted: {Vilhai Maldonado, Nicolás Tibatá}
informed: {Felipe Palacios}
---
# Power BI para componente de arquitectura para visualización y elaboración de dashboard

## Context and Problem Statement

Dentro de la factoría intelignete debe existir un componente de visualización. Una de las funciones de este componente, es permitir que las visualizaciones se realicen en tiempo real tanto del proceso productivo y las órdenes de trabajo.

## Decision Drivers

* Debe permitir crear dashboard con datos del proceso productivo
* Permitir visualizar en tiempo real la información relacionada con las órdenes de trabajo
* Permitir visualizar las analiticas de los sensores en tiempo real, a su vez esta información estará enlazada con el requerimiento funcional MENS-RF6
* Permite visualizar el tiempo real el inventario existente

## Considered Options

Power BI, 
[Looker](MADR_3_1_2.md) , 
[Google data studio](MADR_3_1_3.md)
  

## Pros and Cons of the Options

### Pros

Tiene una interfaz sencilla y amigable con el usuario para la creación y visualización de dashboards. 
Permite integración con otras herramientas dentro de la Nube Azure u otras fuentes de datos. 
Se puede realizar actualización de dashboards en real time, dependendiendo de la fuente de datos que se esté usando. 
Se puede usar como gráficas embebidas en otras plataformas. 


### Cons

Tiene una versión gratutita, pero si se quiere acceder a todas las funciones se debe pagar una licencia por usuario. 
Poca personalización del tipo de gráficas que ofrece
Hay funciones que implican conocimiento previo de cómo funciona la plataforma. 

## More Information

{https://powerbi.microsoft.com/es-es/}
