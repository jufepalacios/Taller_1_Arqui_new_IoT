---
status: {proposed}
date: {2023-06-22}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Vihlai Maldonado, Nicolás Tibatá}
informed: {Juan Palacios}
---

# Patrón State para el módulo de algoritmos de optimización

## Context and Problem Statement

El sistema contará con dos algoritmos inteligentes predictivo para optimizar el volumen de ordenes de trabajo y para la predicción del fallo de una línea de trabajo para reasignar recursos.

## Decision Drivers

* Ejecutar Algoritmo optimizar volumen de órdenes de trabajo.
* Ejecutar Algoritmo optimizar predecir fallo de línea de producto y asignar recurso a otra línea.
* Seleccionar el algoritmo de optimización adecuado en tiempo real.

## Considered Options

* Patron Strategy [Formato MADR](MADR_3_5_1.md)
* Patron State

## Pros and Cons of the Options

### State

Description:

es un patrón de diseño de software que permite que un objeto altere su comportamiento cuando su estado interno cambia.

* Buena, porque promueve la separación de preocupaciones al encapsular los diferentes comportamientos en clases de estado separadas.
* Buena, porque permite que el objeto cliente delegue la lógica del estado a los objetos de estado correspondientes simplificando el objeto cliente.
* Mala, porque hace que sea más dependiente de las implementaciones concretas de los estados y puede requerir cambios en múltiples lugares si se agrega o modifica un estado.
* Mala, porque la gestión de las transiciones de estado puede volverse compleja, especialmente si hay reglas o eventos que deben desencadenar el cambio de estado.
