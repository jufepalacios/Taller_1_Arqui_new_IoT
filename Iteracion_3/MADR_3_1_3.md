---
# These are optional elements. Feel free to remove any of them.
status: {proposed}
date: {2023-06-22}
deciders: {Julián Moreno,Santiago Segura}
consulted: {Vilhai Maldonado, Nicolás Tibatá}
informed: {Felipe Palacios}
---
# Google data studio: Componente de arquitectura para visualización y elaboración de dashboard

## Context and Problem Statement

Dentro de la factoría inteligente debe existir un componente de visualización. Una de las funciones de este componente, es permitir que las visualizaciones se realicen en tiempo real tanto del proceso productivo y las órdenes de trabajo.

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Debe permitir crear dashboard con datos del proceso productivo
* Permitir visualizar en tiempo real la información relacionada con las órdenes de trabajo
* Permitir visualizar las analiticas de los sensores en tiempo real, a su vez esta información estará enlazada con el requerimiento funcional MENS-RF6
* Permite visualizar el tiempo real el inventario existente

## Considered Options

* Google data studio, [PowerBI](MADRD_3_1_1.md), [Looker](MADRD_3_1_2.md)


<!-- This is an optional element. Feel free to remove. -->

## Pros and Cons of the Options

### Pros

Se puede integrar con diferentes fuentes de datos. 
Permite la colaboración en tiempo real entre diferentes usuarios para la elaboración de las visualizaciones. 
Se puede compartir fácilmente los informes, sin necesidad de estar registrado en la plataforma. 

### Cons

Tiene algunas limitaciones en análisis y cálculos complejos.
Los procesos de transformación de datos necesitan de otra herramienta (ETL) que permita hacer modificaciones. 
Está optimizado para conjuntos de datos pequeños y medianos. 

## More Information

https://cloud.google.com/datastudio?hl=es-419
