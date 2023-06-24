---
status: {proposed}
date: {2023-06-22}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Vihlai Maldonado, Nicolás Tibatá}
informed: {Juan Palacios}
---

# Patrón Strategy para el módulo de algoritmos de optimización

## Context and Problem Statement

El sistema contará con dos algoritmos inteligentes predictivo para optimizar el volumen de ordenes de trabajo y para la predicción del fallo de una línea de trabajo para reasignar recursos.

## Decision Drivers

* Ejecutar Algoritmo optimizar volumen de órdenes de trabajo.
* Ejecutar Algoritmo optimizar predecir fallo de línea de producto y asignar recurso a otra línea.
* Seleccionar el algoritmo de optimización adecuado en tiempo real.

## Considered Options

* Patrón Strategy
* Patrón State [Formato MADR](MADR_3_5_1.md)

## Pros and Cons of the Options

### Strategy

Description:

es un patrón de diseño de software que permite definir una familia de algoritmos, encapsular cada uno de ellos en una clase separada y hacer que sean intercambiables.

* Buena, porque proporciona una mayor flexibilidad y adaptabilidad en el código.
* Buena, promueve la reutilización de código.
* Buena, porque facilita el mantenimiento y la comprensión del código.
* Mala, puede haber una creación adicional de objetos para cada estrategia, lo que puede consumir más memoria y recursos.

## More Information
[Patrón Strategy](https://refactoring.guru/design-patterns/strategy)
