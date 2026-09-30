# Ejercicio 1 de Arquitectura de Unreal - MIGUEL DIAZ CHAOUI

En este ejercicio estoy haciendo una pequeña arquitectura para un prototipo de RPG usando Blueprints en Unreal Engine.

La idea es tener una clase base para los objetos con los que el jugador puede interactuar y después crear diferentes objetos a partir de ella. Para esto estoy usando principalmente herencia y composición.

La clase `BP_Interactable` es la base de los objetos interactuables. Tiene una zona de colisión y una función `Interact`, que luego pueden utilizar los diferentes objetos de distintas maneras. Por ejemplo, el NPC utiliza esta función para mostrar un mensaje al jugador y las puertas la utilizarán para abrirse o no dependiendo del tipo de puerta.

Los enemigos están separados de esta clase porque tienen un funcionamiento diferente. Para controlar su vida he creado `BP_HealthComponent` como un componente independiente. Este componente se encarga de controlar la vida del enemigo y avisar cuando llega a cero, momento en el que el enemigo se destruye.

Por ahora tengo hecha la base de los objetos interactuables, el NPC y el enemigo con su sistema de vida y daño.

Todavía falta terminar las puertas de madera y hierro, los botones que abrirán las puertas y los cofres. Después haré las pruebas finales y prepararé el diagrama de la arquitectura para la entrega.

He intentado mantener la arquitectura sencilla y separar las diferentes partes para que sea posible reutilizar la lógica y añadir nuevos objetos sin tener que modificar todo el proyecto.

# Ejercicio 2 - Amplía tu arquitectura

En este ejercicio he ampliado la arquitectura creada en el ejercicio anterior para añadir nuevos comportamientos sin tener que rehacer los elementos que ya funcionaban. He seguido utilizando principalmente herencia y composición para mantener separadas las diferentes responsabilidades.

Para empezar, he terminado los elemenetos del ejercicio 1 que no me dieron tiempo a terminar anteriormente. Estos siendo el `BP_Button` para abrir puetas al pulsar el boton, y `BP_Chest`, que devuleve un mensaje al interactuar con el cofre.

La clase `BP_Interactable` sigue siendo la base de los objetos con los que puede interactuar el jugador. A partir de ella he añadido `BP_Bed`, que utiliza el sistema de vida del jugador para recuperar una cantidad de vida configurable. También he creado `BP_Merchant` como hijo de `BP_NPC`, ya que un comerciante es un tipo de NPC pero necesita un comportamiento diferente al interactuar. En este caso, en lugar de mostrar un mensaje, abre una interfaz que representa la tienda.

Para el sistema de salud he reutilizado `BP_HealthComponent`, que ya se utilizaba para los enemigos en el ejercicio anterior. Se ha ampliado para permitir tanto recibir daño como recuperar vida. Este componente también se utiliza ahora en el jugador, lo que permite reutilizar la misma lógica y evitar crear sistemas de vida diferentes para cada objeto.

Los enemigos también se han ampliado mediante herencia. `BP_NormalEnemy` y `BP_StrongEnemy` heredan de `BP_Enemy`, manteniendo la lógica que ya existía pero permitiendo configurar diferentes cantidades de daño y utilizar diferentes modelos para distinguirlos visualmente.

Para el comerciante he creado `WBP_Shop`, que funciona como una interfaz sencilla de tienda. El comerciante crea y muestra esta interfaz al interactuar con él y el botón de salida permite cerrarla y volver al juego.

De esta forma, la arquitectura anterior se ha podido ampliar reutilizando los sistemas existentes en lugar de duplicarlos. La idea principal ha sido mantener cada responsabilidad separada y utilizar la herencia para crear variantes de objetos que comparten comportamiento, mientras que los componentes permiten reutilizar sistemas como el de salud.

