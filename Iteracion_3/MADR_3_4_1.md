---
status: {accepted}
date: {2023-06-17}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Nicolas Tibatá, Vihlai Maldonado}
informed: {Juan Palacios}
---

# Patrón Singleton para el módulo de generación de órdenes de trabajo.

## Context and Problem Statement

El sistema debe contar con un módulo de generación de órdenes de trabajo que asigne órdenes a operarios, las maquinas que se van a utilizar para fabricar cada componente. Este módulo debería conocer los operarios, las líneas de producción, las maquinas, los componentes y la materia que se utiliza para fabricar cada componente. La información de las ordenes de trabajo y el inventario de la fábrica deben ser guardados en la base de datos.

## Decision Drivers

* CRUD orden de trabajo.
* Almacenar la información de las ordenes de trabajo en BBDD
* Almacenar la información del inventario del material en BBDD

## Considered Options

* Patrón Singleton
* Patrón Factory

## Decision Outcome

Chosen option: "Singleton", porque cumple con las características del problema y no requiere la creación de diferentes clases para cada orden.

### Consequences

* Buena, porque garantiza que solo haya una clase y proporciona un acceso global a ella para que los otros módulos de la arquitectura puedan accederla.
* Buena, porque al solo ser una instancia se garantiza que los recursos compartidos se gestionen de manera eficiente y exista consistencia en la información.
* Buena, porque es fácil de implementar y no requiere de más clases para su funcionamiento.
* Mala, porque si múltiples hilos de ejecución intentan acceder o modificar el Singleton simultáneamente, pueden surgir problemas de concurrencia.

## Pros and Cons of the Options

### Singleton

Description:

el patrón Singleton garantizar que una clase tenga una única instancia y proporcionar un punto de acceso global a esa instancia. 

* Buena, porque permite un control más preciso sobre cómo se accede y utiliza la instancia en el código.
* Buena, porque al ser accesible globalmente, la instancia Singleton se puede utilizar fácilmente en cualquier parte del código donde se requiera.
* Mala, porque puede dificultar las pruebas unitarias ya que puede ser complicado aislar y probar las clases que dependen del Singleton.
* Mala, puede dificultar la extensibilidad y la herencia de la clase Singleton.

## More Information
[Singleton](https://refactoring.guru/design-patterns/singleton)
