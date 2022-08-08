# El Folder Hell
Hay veces en la que pasamos por alto nuestra estructura de carpetas, haciendo que despues del pasar del tiempo nos olvidemos que es lo que contienen.

Que tire la primera piedra o que tire produccion en este mismo momento quien no lo haya realizado.

# ¿Qué es el Folder Hell?

El Folder Hell es un problema bastante común en el desarrollo de software, especialmente
cuando pensamos que va a ser una aplicación que no va a necesitar escalar en un futuro, 
y por ende tendemos a simplificar demasiado la estructura de carpetas principalmente
para que no se vea tan complicado el desarrollo.

Un ejemplo de esto es el famoso proyecto en el que usamos el anti-patrón de MVC (Modelo Vista Controlador), por un lado tenemos nuestro modelo, por otro nuestro controlador, y por último nuestra vista/servicio.

Por eso, en el caso de que supongamos que la aplicación no vaya a escalar a futuro, optamos por simplificar la estructura de carpetas.

```
src/
├── controllers/
│   ├── homeController.ts
│   ├── userController.ts
│   ├── algoController.ts
│   └── ...
├── models/
│   ├── homeModel.ts
│   ├── userModel.ts
│   ├── algoModel.ts
│   └── ...
├── services/
│   ├── homeService.ts
│   ├── userService.ts
│   ├── algoService.ts
│   └── ...
└── index.ts
```

El problema es que si queremos agregar un nuevo controlador, modelo, servicio, etc,
vamos a empezar a sobrecargar la estructura de carpetas, y por ende, a complicar el desarrollo. Vamos a agregar más carga a los controladores, modelos, servicios, etc. logrando tener una estructura de carpetas muy simple, pero con mucha carga y difícil búsqueda/lectura/edición.

**No nos tenemos que olvidar que esto ataca directamente a el naming convention de los archivos, y por ende, a la legibilidad del código.**


# ¿Cómo se puede hacer para que la estructura de las carpetas sea más simple?

Este problema se puede solucionar con una estructura de carpetas que a lo largo de la vida del proyecto, nos permita escalar a nivel de implementación de una forma mucho más amena para los desarrolladores.

Esto se logra dividiendo nuestra "arquitectura" si quiere llamarse así, en módulos, los cuales van a cumplir con responsabilidades específicas, y que van a tener una estructura de carpetas muy simple, con una carga muy baja, y con una fácil lectura y búsqueda.

```
src/
├── modules/
│   ├── home
│   ├── user
│   ├── algo
│   └── ...
```

Dentro de cada módulo, vamos a tener un archivo para cada controlador, modelo, servicio, etc.. Usando un naming convention para los archivos, el cual nos simplifique la búsqueda de en donde podemos llegar a tener un problema.

```
src/
├── modules/
│   ├── home
│   │   ├── home.controller.ts
│   │   ├── home.model.ts
│   │   ├── home.service.ts
│   │   └── ...
│   ├── user
│   │   ├── user.controller.ts
│   │   ├── user.model.ts
│   │   ├── user.service.ts
│   │   └── ...
│   ├── algo
│   │   ├── algo.controller.ts
│   │   ├── algo.model.ts
│   │   ├── algo.service.ts
│   │   └── ...
│   └── ...
└── index.ts
```

# Ya tengo mi proyecto modularizado, que pasa si tengo que agregar módulos hijos?

Podemos agregar módulos hijos a nuestros módulos padres, y así logrando nuevamente, una estructura de carpetas muy simple, con una carga muy baja, y con una fácil lectura y búsqueda.

Usemos de ejemplo una aplicación que tiene 2 tipos de usuarios, un usuario sería el consumidor final y por otro lado, un usuario el cual va acceder al panel de administración de la aplicación. Estos 2 usuarios comparten muy pocas cosas entre sí, pero de forma muy resumida, uno es un usuario interno y el otro es un usuario externo.

Lo único que comparten entre ellos, es que al final del dia, van a ser usuarios


```
src/
├── modules/
│   ├── user
│   │   ├── user.controller.ts
│   │   ├── user.model.ts
│   │   ├── user.service.ts
│   │   ├── user-panel
│   │   │   ├── user-panel.controller.ts
│   │   │   ├── user-panel.model.ts
│   │   │   ├── user-panel.service.ts
│   │   │   └── ...
│   │   └── user-external
│   │       ├── user-external.controller.ts
│   │       ├── user-external.model.ts
│   │       ├── user-external.service.ts
│   │       └── ...
│   └── ...

```

# ¿Qué beneficios tiene este modelo?

El modelo es una buena herramienta para el desarrollo de software, ya que nos permite separar el trabajo de la lógica de negocio, y de esta forma, podemos hacer el trabajo más sencillo, más eficiente, más escalable y mucho más importante, más ágil a la hora de implementar nuevas funcionalidades.


