---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-22}
deciders: {Julián Moreno,Santiago Segura}
consulted: {Vilhai Maldonado, Nicolás Tibatá}
informed: {Felipe Palacios}
---
# Looker:Componente de arquitectura para visualización y elaboración de dashboard

## Context and Problem Statement

Dentro de la factoría inteligente debe existir un componente de visualización. Una de las funciones de este componente, es permitir que las visualizaciones se realicen en tiempo real tanto del proceso productivo y las órdenes de trabajo.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Debe permitir crear dashboard con datos del proceso productivo
* Permitir visualizar en tiempo real la información relacionada con las órdenes de trabajo
* Permitir visualizar las analiticas de los sensores en tiempo real, a su vez esta información estará enlazada con el requerimiento funcional MENS-RF6
* Permite visualizar el tiempo real el inventario existente

## Considered Options

* Looker , [PowerBI](MADR_3_1_1.md), [Google data Studio](MADR_3_2_1.md) 


## Pros and Cons of the Options

### Pros

Interfaz intuitiva para la consulta de los dashboards. 
Tiene un modelado de  datos flexibles ya que cuenta con su propio lenguaje, denominado LookML.
Permite a los usuarios hacer consultas directas sobre las fuentes de datos por medio de SQL a los usurios. 
Los dashboards realizados se pueden compartir entre usuarios. 

### Cons

Tiene una versión gratutita, y una version empresarial por la que hay que realizar un pago.  
No es una de las herramientas más intuitivas para la construcción de visualizaciones gráficas.
No hay versión offline, se necesita siempre estar conectado a internet para acceder a las visualizaciones de los datos.  

## More Information

{https://cloud.google.com/looker?hl=es}
