# Informe de Investigación Sobre Arquitectura de Computadoras

Electronica IV - TP - Arquitectura de Computadora

Ganem Elías

## Introducción
Antes de comenzar se indicará a que hacen referencias palabras del lenguaje técnico que hay que conocer antes de introducirse en el tema:
- **Assembler  o Ensamblador** es el encargado de llevar un programa escrito en lenguaje assembler a lenguaje maquina.
- **Programa Fuente** un programa escrito en un lenguaje distinto al lenguaje maquina. 
- **Programa Objeto** es el resultado de la traducción de un programa fuente a lenguaje maquina. 
- **Compilador** es el que traduce un lenguaje de alto nivel a lenguaje assembler.
- **Lenguaje Maquina** en este las instrucciones están en binario.
- **Lenguaje de Alto Nivel** es un leguaje mas parecido al ingles, por enzima del lenguaje assembler .Cada computadora necesita su propio compilador / assembler, de esta forma *el lenguaje de alto* nivel es independiente de la computadora que se desea programar.
- **Sistema Operativo** es un programa que se encarga de controlar el hardware y permite la interacción de un programa con este.
> (Floyd)

### Computadora
Una computadora esta formada por los siguientes elementos conectados entre sí por 3 *buses* internos:
- **CPU**: (Central Proccessing Unit) controla todo lo que hace la computadora, se le llama *procesador*. Este ejecuta instrucciones dadas a través de un *programa* guardado en una memoria.
- **Memoria** hay de varios tipos, pero los mas básicos son:
	- **RAM**: (ramdon access memory) es una memoria que se puede escribir y leer, es *volátil* por lo que si se desconecta la computadora de su alimentación se pierde el contenido de esta. Se utiliza para guardar datos
	- **ROM**: (read only memory) es una memoria que solo puede ser leída, es *no volátil* por lo que si se desconecta la alimentación de la computadora no se pierde su contenido. También se le llama *firmware* porque suele contener un software que está permanentemente en ella. Por lo general contiene la *BIOS*.
	- **Caché**: es una memoria ram que posee datos a los que se accede de forma frecuente y permite tener un acceso mas rápido a estos.
- **Puertos de entrada/salida**: es una conexión física que posee la computador para enviar y recibir información de dispositivos externos a esta llamados **periféricos**, que le permiten interactuar con el exterior.

Un **Bus** es una conexión que tiene especificaciones eléctricas particulares, lo que permite que ambos puntos de conexión puedan tener una comunicación eficiente. Los tipos básicos son:
- *Bus de Direcciones*: es utilizado por el CPU para seleccionar direcciones de memoria o puertos.
- *Bus de Datos*: permite enviar instrucciones del programa y datos entre el CPU, las memorias y los puertos. 
- *Bus de Control*: es usado para enviar y recibir señales de control desde y para el CPU.

Además anteriormente se mencionaron unos conceptos que es importante saber a que hacen referencia:
- **Programa**: conjunto de instrucciones que ejecuta el microprocesador de forma secuencial.
- **Bios**: (Basic input/output system) contiene un programa que tiene que ser ejecutado ni bien se alimente la computadora, el cual se encarga de establecer un funcionamiento inicial de la computadora antes de arrancar a ejecutar algún programa o el *sistema operativo*.
> (Floyd)

## Microprocesador
Es un circuito integrado digital que se programa para realizar operaciones y tomar decisiones con datos. Puede hacer operaciones aritméticas y lógicas. Está formado por 4 partes básicas: *ALU, decodificador de instrucciones, registros y unidad de control*. La forma en la que estas partes están interconectadas se llama **arquitectura de la computadora**, esto determina las instrucciones y como se ejecución. A continuacion se explica cada una de las partes basicas:
- ALU: Esta se encarga de realizar las operaciones aritméticas y lógicas con los datos que obtiene de los registros.
- Decodificador de Instrucciones: Se encarga de traducir las instrucciones que están en la memoria para saber que debe hacer el microprocesador.
- Registros: Los registros forman una matriz que contiene datos e instrucciones, a los cuales la ALU puede acceder rápidamente. Hay tres tipos de registros:
    - de propósito general: son aquellos que pueden ser usados por el programa como se desee.
    - específicos: no pueden usarse como los anteriores, estos poseen una función en particular como por ejemplo indicadores de alguna condición de la ALU.
    - invisibles: son aquellos a los que no se posee acceso, son usados por el microprocesador.
- Unidad de Control: Se encarga de sincronizar el funcionamiento de todos los elementos del microprocesador
> (Floyd)

Ahora con estos coneptos, podemos hacer las siguientes distinciones:
- **Arquitectura de la Computadora** son las características a las que posee acceso el programador, y afectan la ejecución del programa, también se le llama **Set de Instrucciones de la Arquitectura (ISA)**.
- **Organización de la Computadora** hace referencia a los elementos de la computadora y como se interconectan entre ellos, esto da las especificaciones de la arquitectura.
> (William Stallings)

Hay que saber que el hardware de una computadora solo puede ejecutar instrucciones simples de bajo nivel. Para ir de estas instrucciones a una aplicación es necesario tener capas de **software** que traduzcan lo que hace la aplicación (que es un alto nivel) a instrucciones simples para el hardware. El **sistema operativo** es un software que genera una interfaz entre un programa y el hardware, además posee varios servicios y funciones de supervisión
> (Patterson)


## Clases de arquitectura de computadora

A continuacion se expondrán distintos tipos de arquitecturas
### Arquitectura Harvard
La arquitectura Harvard almacena instrucciones y datos en memorias separadas. La instrucción se lleva a la CPU en un solo acceso a la memoria de programa a través del bus de instrucciones, mientras tanto el bus de datos está libre y puede accederse a través de él a los datos que se necesitan para ejecutar la instrucción anterior. Al tener 2 buses separados, el bus de instrucciones es más ancho que el bus de datos. Esto permite que las instrucciones se codifiquen en palabras de más de 8 bits.
### Arquitectura Von Neumann
La característica más destacada de la arquitectura Von Neumann es que el acceso a la memoria de datos e programa se realiza por el mismo bus, es decir no es necesario que los datos e instrucciones estén en la misma memoria. Requiere acceso (o varios accesos) a memoria para traer la instrucción. Si esta instrucción maneja datos de memoria, se debe realizar otro acceso para traer, operar y volver a almacenar los datos. En la arquitectura Von Neumann se necesitan habitualmente varios paquetes de 8 bits para codificar una instrucción.

Para comparar ambas arquitecturas se realizó el siguiente cuadro:
|Harvard               | Von Neumann              |
|--------------------- | ------------------------ |
| Posee un bus de datos para instrucciones y otro para datos, por lo que puede demorarse menos tiempo en ejecutar una instrucción. | Reduce el costo al usar el mismo bus para datos e isntrucciones. |
| Permite el uso de pipelined.                                                                                                     | Al tener un solo bus su implementación es más sencilla.          |

> ([Estructura de Computadores](https://cv.uoc.edu/annotation/8255a8c320f60c2bfd6c9f2ce11b2e7f/619469/PID_00218228/PID_00218228.html))

Según como se almacenan los operandos en la CPU el procesador puede ser:
- Maquina de Pila: donde los operandos se almacenan en una pila, por lo que los operandos estan disponibles en la pila.
- Maquina de Acumulador, hay que saber que **acumulador** es un en el que son almacenados temporalmente los resultados aritméticos y lógicos intermedios que serán tratados por el la ALU. En estas maquinas un operando está implícitamente en el acumulador siempre leyendo e ingresando datos.
- La maquina de registros tiene solo operandos en registros o memoria.

 Ventajas de  cada una
- **Pila**:
    - Modelo sencillo para evaluación de expresiones.
    - Instrucciones cortas pueden dar una buena densidad de código.
- **Acumulador**:
    - Instrucciones cortas.
    - Minimiza estados internos de la máquina (unidad de control sencilla).
- **Registro**:
    - Modelo más general para el código de instrucciones parecidas.
    - Automatiza generación de código y la reutilización de operandos.
    - Reduce el tráfico a memoria.
    - El acceso a los datos es más rápido y veloz.

Desventajas
- **Pila**:
    - A una pila no se puede acceder aleatoriamente.
    - Esta limitación hace difícil generar código eficiente.
- **Acumulador**:
    - Como el acumulador es solamente almacenamiento temporal.
- **Registro**:
    - Todos los operadores deben ser nombrados, conduciendo a instrucciones más largas.

> (Wikipedia)

Como se mencionó antes la arquitectura determina el set de instrucciones, hay dos grupos de set de instrucciones:
- CISC manejan  un gran número de instrucciones complejas, es decir, con gran variedad de tipos de datos, de modos de direccionamiento y de operaciones. Esto permite implementar instrucciones de alto nivel directamente o con un número pequeño de instrucciones ensamblador.
- RISC, está compuesto por pocas instrucciones y muy básicas. Se trata de instrucciones simples y ortogonales, en los que los formatos de instrucción son uniformes y se utilizan pocos tipos de datos y de modos de direccionamiento. Además son fácilmente extensibles y por tanto, permiten diseñar nuevos repertorios con o modificaciones y/o extensiones de repertorios ya existentes.

También se debe de tener en cuenta que el hardware de procesadores RISC es mucho más sencillo de diseñar, más barato y puede trabajar a mayor frecuencia de reloj. Y quizás lo más importante: las técnicas de optimización son mucho más sencillas de implementar, tanto en el propio hardware del procesador como en el compilador. Todo esto compensa la principal desventaja que implican estos repertorios tan sencillos, que siempre necesitan un mayor número de instrucciones que un repertorio CISC para realizar la misma tarea.

> (Beltrán)

## ARM
La arquitectura ARM viene de los principios de diseño RISC y es usada en sistemas embebidos. Su set de instrucciones fue diseñado para tener una implementación y ejecución eficiente.
*Arm Holdings* otorga licencias para varios microprocesadores especializados y tecnologías relacionadas, pero la mayor parte de su línea de productos es la familia Cortex de arquitecturas de microprocesadores.
### Cortex
Es una familia de arquitectura de microprocesadores ARM. Hay tres tipos de arquitectura Cortex:
- Cortex A: son de procesadores de aplicación. Y poseen soporte de "memory managment unit MMU" que es necesario para sistemas operativos moviles.
- Cortex R: son para aplicaciones de tiempo real, es decir se necesita una respuesta rápida ante los eventos. Tiene un tiempo de respuesta muy bajo. La mayoria no tiene MMU, pero poseen "Memory Protection Unit MPU" que es un modulo de hardware que evita que un programa acceda sin querer a la memoria asignada para otro programa.
- Cortex M: fueron desarrollados para microcontroladores, poseen MPU y no MMU. Solo usan el set de instrucciones thumb solamente. Hay siete versiones de esta:
	1. Cortex-M0: diseñada para aplicaciones de 8 y 16 bits. Se caracteriza por su bajo costo, bajo consumo y simplicidad
	2. Cortex-M0+: es una mejora del anterior en cuanto a eficiencia energética.
	3. Cortex-M3 : diseñada para aplicaciones de 16 y 32 bits, se centra en el rendimiento y eficiencia energetica. Posee funciones de debug y seguimiento.
	4. Cortex-M4: tiene todo lo que posee el anterior, pero tiene instrucciones que soportan el procesamiento digital de señales.
	5. Cortex-M7: tiene mejor rendimiento que el M4, es de 32bits pero posee buses e instrucciones de 64bits.
	6. Cortex-M23: es parecido a M0+ pero instrucciones de división de enteros.
	7. Cortex-M33: es como M4 solo que añade caracteristicas de seguridad.

#### Cortex M3
Posee buses de señal y de instrucciones separadas, es decir es una arquitectura Harvard. El **Nucleo**, parte del procesador Cortex-M2, contiene:
- Decodificador de instrucciones Thumb
- ALU que soporta multiplicación y división por hardware.
- Lógica de Control
- Interfaces a otros componentes del procesador.

Notar que el termino *núcleo o core* y procesador son distintos. El procesador posee más elementos que el core como:
- NVIC permite el manejo de instrucciones configurables.
- ETM un componente de depuración que permite la deconstrucción de una ejecución de programa.
- Debug acces port (DAP) permite tener un acceso de forma externa a la depuración.
- SRAM y periféricos.
- Memory Protection Unit protege datos usados por el sistema operativo de aplicaciones del usuario, evita el acceso a regiones de memoria, permite definir regiones de memoria como de solo lectura y detecta accesos inesperados a la memoria que podrían romper el sistema.

> (William Stallings)

## Conclusiones

Se puede concluir que la aqruitectura es lo basico que debe saber el programador para realizar su programa, como el tipo de instrucciones que debe de usar. Esto tambien le da una idea de como funciona el dispositivo  progrmar. Pero hay que distinguir esto con la organizacion de la computadora que es la forma en la que se interconectan los elementos de dicho dispositivo y que tipo de elementos posee.

Si se descompone un sistema de computo, la arquitectura estaría en un nivel medio, pues considerando los distintos niveles de abstraccion este estaría mucho antes de un sistema operativo y un poco despues de hacer una abtraccion del funcionamiento del microproceasdor o microcontrolador.

La funcion de la arquitectura es brindar al programador los conocimientos y herramientas necesarias para poder programar y trabrajar con el micro sin tener ningun problema.

Antes de elegir una arquitectura se debería ver que es lo que necesito, es decir para que se va a usar el micro y que forma de programar haría más eficiente el trabajo a partide de esto se elegirá la arquitectura que más se adapte a estas necesidades.


## Bibliografía
- William Stallings. Computer Organization and Architecture (11th edition). Pearson.
- Patterson & Hennessy. Computer Organization and Architecture Risc-V (2nd edition). El sevier.
- Patterson & Hennessy. Computer Organization and Architecture A quantitative Approach (6th edition). El sevier.
- Floyd. Fundamentos de Sistemas Digitales(9a edición)
- [Wikipedia](https://es.wikipedia.org/wiki/Arquitectura_de_computadoras)
- [Estructura de Computadores](https://cv.uoc.edu/annotation/8255a8c320f60c2bfd6c9f2ce11b2e7f/619469/PID_00218228/PID_00218228.html)
