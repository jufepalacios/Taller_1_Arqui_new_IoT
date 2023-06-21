---
status: {accepted}
date: {2023-06-17}
deciders: {Julian Moreno, Santiago Segura}
consulted: {Nicolas Tibatá, Vihlai Maldonado}
informed: {Juan Palacios}
---

# Selección de Estilo de arquitectura para la factoría

## Context and Problem Statement
Una factoría 4.0 desea implementar un software que sea capaz de crear y asignar ordenes de trabajo a sus operarios en sus 3 líneas de producción y registrar el comportamiento de estas por medio de sensores IoT. Ademas, estos datos deberán poder ser visualizados para analizar el estado de las líneas de producción. Dicha información deberá ser de fácil acceso para todos en la factoría por medio de un sistema de mensajería. Finalmente, el software debería ser capaz de predecir y tomar acción ante algún fallo de una línea de producción y optimizar el volumen de ordenes de trabajo.

## Decision Drivers

* Almacenamiento – Almacenar la información recopilada por los sensores, el inventario y las órdenes de trabajo.
* Visualización – Dashboard para visualizar los datos de la factoría en tiempo real.
* Órdenes de trabajo – Asignación de ordenes por operario y maquinas para fabricar componentes.
* Optimización – Evaluación y ejecución de los algoritmos de predicción.
* Canal de transmisión – Comunicación entre los paquetes del sistema.
* Lectura y Procesamiento – Capturar los valores registrados por los diferentes sensores y procesar su información.


## Considered Options

* Estilo por eventos (EDA, Event-Driven Architecture)
* Estilo MODEL-VIEW-CONTROLLER (MVC)

## Decision Outcome

Chosen option: "Estilo por eventos: EDA", porque resuelve todos los requerimientos funcionales.

### Consequences

* Buena, porque es fácil agregar emisores y consumidores de eventos.
* Buena, porque se puede distribuir el evento de forma ramificada a los consumidores y estos pueden procesarlo en paralelo con un propósito diferente.
* Buena, porque permite supervisar y recibir alertas sobre cualquier anomalía, cambio o actualización en los eventos.
* Mala, porque se debe garantizar la entrega de los eventos, no se pueden perder.  


## Pros and Cons of the Options

### Estilo por eventos

Descripción:
Se basa en la detección, consumo y reacción a eventos, que representa un cambio significativo en el estado de un sistema.

* Buena, porque los componentes se comunican a través de eventos, lo que les permite estar desacoplados entre sí. Esto mejora la flexibilidad, escalabilidad y mantenibilidad.
* Buena, porque permite procesamiento asíncrono y con ello mejorar el rendimiento y la capacidad de respuesta del sistema.
* Buena, porque los eventos pueden procesarse inmediatamente después de producirse, lo que permite actualizaciones en tiempo real, notificaciones instantáneas y reacciones rápidas a condiciones cambiantes.
* Mala, porque coordinar el flujo de eventos y gestionar las suscripciones a los mismos requiere un diseño y una implementación cuidadosos.
* Mala, porque los eventos perdidos o descartados pueden provocar incoherencias en los datos o acciones perdidas.

### Estilo MODEL-VIEW-CONTROLLER

Descripción
comúnmente utilizado para desarrollar interfaces de usuario que divide la lógica del programa relacionado en tres elementos interconectados.

* Buena, porque los componentes de visualización, modelo y controlador se encuentran separados y esto hace que se pueden gestionar y realizar cambios en cualquiera de ellos sin interferir en los otros.
* Buena, porque es escalable ya que se pueden editar individualmente los componentes. 
* Mala, porque puede agregar complejidad a aplicaciones pequeñas o a problemas donde no se puedan identificar las partes de visualización, modelo y controlador.
* Mala, porque la comunicación entre los tres componentes podría requerir recursos adicionales y mayor tiempo de procesamiento por lo que afecta el rendimiento.

## More Information

[Mayor información sobre EDA](info/More_Information.md)
