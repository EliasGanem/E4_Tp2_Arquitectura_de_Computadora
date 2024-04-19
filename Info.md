# Computadora
Una computadora esta formada por los siguientes elementos conectados entre sí por 3 *buses* internos:
- **CPU**: (Central Proccessing Unit) controla todo lo que hace la computadora, es un *microprocesador* que se ejecuta instrucciones dadas a través de un *programa* guardado en una memoria.
- **Memoria** hay de varios tipos, pero los mas básicos son:
	- **RAM**: (ramdon access memory) es una memoria que se puede escribir y leer, es *volátil* por lo que si se desconecta la computadora de su alimentación se pierde el contenido de esta. Se utiliza para guardar datos
	- **ROM**: (read only memory) es una memoria que solo puede ser leída, es *no volátil* por lo que si se desconecta la alimentación de la computadora no se pierde su contenido. También se le llama *firmware* porque suele contener un software que está permanentemente en ella. Por lo general contiene la *BIOS*.
	- **Caché**: es una memoria ram que posee datos a los que se accede de forma frecuente y permite tener un acceso mas rápido a estos.
- **Puertos de entrada/salida**: es una conexión física que posee la computador para enviar y recibir información de dispositivos externos a esta llamados **periféricos**, que le permiten interactuar con el exterior.

**Buses**: es una conexión que tiene especificaciones eléctricas particulares, lo que permite que ambos puntos de conexión puedan tener una comunicación eficiente. Los tipos básicos son:
- *Bus de Direcciones*: es utilizado por el CPU para seleccionar direcciones de memoria o puertos.
- *Bus de Datos*: permite enviar instrucciones del programa y datos entre el CPU, las memorias y los puertos. 
- *Bus de Control*: es usado para enviar y recibir señales de control desde y para el CPU.

**Programa**: conjunto de instrucciones que ejecuta el microprocesador de forma secuencial.
**Bios**: (Basic input/output system) contiene un programa que tiene que ser ejecutado ni bien se alimente la computadora, el cual se encarga de establecer un funcionamiento inicial de la computadora antes de arrancar a ejecutar algún programa o el *sistema operativo*.

## Microprocesador
Es un circuito integrado digital que se programa para realizar operaciones y tomar decisiones con datos. Puede hacer operaciones aritméticas y lógicas. Está formado por 4 partes básicas: *ALU, decodificador de instrucciones, registros y unidad de control*. La forma en la que estas partes están interconectadas se llama **arquitectura de la computadora**, esto determina las instrucciones y como se ejecución.

### ALU
Esta se encarga de realizar las operaciones aritméticas y lógicas con los datos que obtiene de los registros.
### Decodificador de Instrucciones
Se encarga de traducir las instrucciones que están en la memoria para saber que debe hacer el microprocesador.

### Registros
Los registros forman una matriz que contiene datos e instrucciones, a los cuales la ALU puede acceder rápidamente. Hay tres tipos de registros:
- de propósito general: son aquellos que pueden ser usados por el programa como se desee.
- específicos: no pueden usarse como los anteriores, estos poseen una función en particular como por ejemplo indicadores de alguna condición de la ALU.
- invisibles: son aquellos a los que no se posee acceso, son usados por el microprocesador.

### Unidad de Control
Se encarga de sincronizar el funcionamiento de todos los elementos del microprocesador


## Pipelining
Permite que al mismo tiempo se estén ejecutando varias instrucciones. Uno de los primeros microprocesadores de Intel poseían:
- una **unidad de ejecución EU** que se encargaba de realizar la instrucción.
- una **unidad de interfaz de bus BIU** se encargaba del bus de datos, según lo que le comandaba la EU, leer la nueva instrucción y escribir los resultados.
Por lo que mientras uno ejecuta la instrucción el otro se adelanta y busca la siguiente instrucción. A este método de trabajo se le llama **precarga** o **pipelining**.

>El *pipelining* permite que el procesador trabaje constantemente y no necesite esperar a tener la instrucción para empezar a trabajar. Sino que una parte se encarga de ver que es lo que se desea hacer mientras que la otra está haciendo lo que le decía la instrucción anterior.

Las instrucciones que se deben ejecutar a continuación se almacenan en una memoria interna muy rápida a la que se llama **cola de instrucciones**. Lo que permite que la EU posea tapidamente la siguiente instrucción.
También se puede tener mas unidades de ejecución.

# William Stallings

**Arquitectura de la Computadora** son las características a las que posee acceso el programador, y afectan la ejecución del programa, también se le llama **Set de Instrucciones de la Arquitectura (ISA)**.
**Organización de la Computadora** hace referencia a los elementos de la computadora y como se interconectan entre ellos, esto da las especificaciones de la arquitectura.

## ARM
La arquitectura ARM viene de los principios de diseño RISC. Su set de instrucciones fue diseñado para tener una implementación y ejecución eficiente. Todas las instrucciones son de 32bits.
Thumb es un subconjunto de instrucciones ARM recodificada para instrucciones de 16bits, diseñado para aumentar el rendimiento de implementaciones ARM con bus de 16bits o menos.

### Cortex
es una familia de arquitectura de microprocesadores ARM. Hay tres tipos de arquitectura Cortex:
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

Notar que el termino núcleo y procesador son distintos. El procesador posee mas elementos que el core como:
- NVIC permite el manejo de instrucciones configurables.
- ETM un componente de depuración que permite la deconstrucción de una ejecución de programa.
- Debug acces port (DAP) permite tener un acceso de forma externa a la depuración.
- SRAM y periféricos.
- Memory Protection Unit protege datos usados por el sistema operativo de aplicaciones del usuario, evita el acceso a regiones de memoria, permite definir regiones de memoria como de solo lectura y detecta accesos inesperados a la memoria que podrían romper el sistema.


# Terminología de Interés
**Assembler  o Ensamblador** es el encargado de llevar un programa escrito en lenguaje assembler a lenguaje maquina.
**Programa Fuente** un programa escrito en un lenguaje distinto al lenguaje maquina. 
**Programa Objeto** es el resultado de la traducción de un programa fuente a lenguaje maquina. 
**Compilador** es el que traduce un lenguaje de alto nivel a lenguaje assembler.
**Lenguaje Maquina** en este las instrucciones están en binario.
**Lenguaje de Alto Nivel** es un leguaje mas parecido al ingles, por enzima del lenguaje assembler .Cada computadora necesita su propio compilador / assembler, de esta forma *el lenguaje de alto* nivel es independiente de la computadora que se desea programar
