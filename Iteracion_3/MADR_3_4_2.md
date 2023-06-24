---
status: {proposed}
date: {2023-06-22}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Nicolas Tibatá, Vihlai Maldonado}
informed: {Juan Palacios}
---

# Patrón Factory para el módulo de generación de órdenes de trabajo.

## Context and Problem Statement

El sistema debe contar con un módulo de generación de órdenes de trabajo que asigne órdenes a operarios, las maquinas que se van a utilizar para fabricar cada componente. Este módulo debería conocer los operarios, las líneas de producción, las maquinas, los componentes y la materia que se utiliza para fabricar cada componente. La información de las ordenes de trabajo y el inventario de la fábrica deben ser guardados en la base de datos.

## Decision Drivers

* CRUD orden de trabajo
* Almacenar la información de las ordenes de trabajo en BBDD
* Almacenar la información del inventario del material en BBDD

## Considered Options

* Patrón Singleton [Formato MADR](MADR_3_4_1.md)
* Patrón Factory

## Pros and Cons of the Options

### Factory

Description:

es un patrón de diseño creacional que se utiliza para crear objetos de diferentes tipos sin especificar directamente su clase concreta. Proporciona una interfaz común para crear objetos, pero permite a las subclases decidir qué clase concreta instanciar.

* Buena, porque proporciona una forma flexible de crear objetos sin acoplar el código a clases concretas.
* Buena, facilita la incorporación de nuevos tipos de objetos sin afectar el código existente.
* Mala, puede agregar cierta complejidad al código, especialmente si hay múltiples tipos de objetos y fábricas.
* Mala, implica la creación de clases adicionales, como las fábricas, lo que puede resultar en un mayor número de clases en el código.
