Ejercicio 1 de Arquitectura de Unreal - MIGUEL DIAZ CHAOUI

En este ejercicio estoy haciendo una pequeña arquitectura para un prototipo de RPG usando Blueprints en Unreal Engine.

La idea es tener una clase base para los objetos con los que el jugador puede interactuar y después crear diferentes objetos a partir de ella. Para esto estoy usando principalmente herencia y composición.

La clase `BP_Interactable` es la base de los objetos interactuables. Tiene una zona de colisión y una función `Interact`, que luego pueden utilizar los diferentes objetos de distintas maneras. Por ejemplo, el NPC utiliza esta función para mostrar un mensaje al jugador y las puertas la utilizarán para abrirse o no dependiendo del tipo de puerta.

Los enemigos están separados de esta clase porque tienen un funcionamiento diferente. Para controlar su vida he creado `BP_HealthComponent` como un componente independiente. Este componente se encarga de controlar la vida del enemigo y avisar cuando llega a cero, momento en el que el enemigo se destruye.

Por ahora tengo hecha la base de los objetos interactuables, el NPC y el enemigo con su sistema de vida y daño.

Todavía falta terminar las puertas de madera y hierro, los botones que abrirán las puertas y los cofres. Después haré las pruebas finales y prepararé el diagrama de la arquitectura para la entrega.

He intentado mantener la arquitectura sencilla y separar las diferentes partes para que sea posible reutilizar la lógica y añadir nuevos objetos sin tener que modificar todo el proyecto.
