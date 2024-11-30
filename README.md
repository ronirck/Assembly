# Assembly Personal Documentation

> By Miguelangel Vasquez

## Assembly

Es un lenguaje de programación de bajo nivel que utiliza mnemónicos para representar las instrucciones que se ejecutarán directamente en el
procesador. Cada instrucción en ensamblador corresponde a una operación específica del hardware, como sumar números, mover datos en la
memoria o saltar a otra parte del código.

### <ins>Características</ins>

-   **Muy cercano al hardware** : Permite un control muy preciso sobre el funcionamiento del procesador y otros componentes. Dependiente de
    la arquitectura: Cada tipo de procesador (x86, ARM, etc.) tiene su propio lenguaje ensamblador. Dificultad: Es considerado un lenguaje
    de programación difícil de aprender y utilizar debido a su bajo nivel de abstracción y la necesidad de conocer a fondo la arquitectura
    del procesador.

-   **Dependiente de la arquitectura** : Cada tipo de procesador (x86, ARM, etc.) tiene su propio lenguaje ensamblador.

-   **Dificultad** : Es considerado un lenguaje de programación difícil de aprender y utilizar debido a su bajo nivel de abstracción y la
    necesidad de conocer a fondo la arquitectura del procesador.

## MIPS32

MIPS32 es una arquitectura de microprocesador de 32 bits, lo que significa que puede procesar datos en unidades de 32 bits (4 bytes). Es
parte de la familia MIPS, una serie de microprocesadores diseñados para ser eficientes y fáciles de implementar.

### <ins>Características</ins>

-   **Arquitectura RISC** : MIPS es una arquitectura RISC (Reduced Instruction Set Computer), lo que implica que tiene un conjunto de
    instrucciones reducido y optimizado, lo que la hace más sencilla y rápida.

-   **Registros** : Utiliza un gran número de registros generales para almacenar datos, lo que reduce la necesidad de acceder a la memoria
    con frecuencia, mejorando el rendimiento.

-   **Formato de instrucción fijo** : Todas las instrucciones tienen el mismo tamaño, lo que facilita la decodificación y ejecución.

-   **Pipeline** : Emplea un pipeline de ejecución para procesar múltiples instrucciones en paralelo, aumentando la velocidad.

-   **Endianness** : Puede ser tanto big-endian como little-endian, dependiendo de la implementación.

### <ins>Porque MIPS32</ins>

-   **Simplicidad** : Su diseño sencillo la hace fácil de aprender y enseñar, convirtiéndola en una arquitectura popular para la educación y
    el desarrollo de sistemas embebidos.

-   **Rendimiento** : A pesar de su simplicidad, MIPS32 ofrece un buen rendimiento en muchas aplicaciones.

-   **Flexibilidad** : Se ha utilizado en una amplia variedad de dispositivos, desde sistemas embebidos hasta consolas de videojuegos.

### <ins>Relación Assembly-MIPS32</ins>

-   MIPS32 es como el plano arquitectónico de la casa, define la estructura básica, las habitaciones, las conexiones entre ellas, etc.
    Establece las reglas y las posibilidades de lo que se puede construir.

-   Assembly es el lenguaje que utilizamos para dar las instrucciones precisas a los albañiles para que construyan la casa siguiendo ese
    plano. Es decir, el assembly utiliza las "instrucciones" definidas por la arquitectura MIPS32 para crear programas específicos.

## MARS

MARS, que significa MIPS Assembler and Runtime Simulator, es un software diseñado específicamente para ensamblar y ejecutar programas
escritos en lenguaje ensamblador MIPS.

### <ins>Porque MARS</ins>

-   **Enseñanza**: Es una herramienta fundamental en cursos universitarios de arquitectura de computadoras y sistemas operativos. Permite a
    los estudiantes experimentar de forma práctica cómo funciona un procesador a nivel de instrucción.

-   **Aprendizaje**: Facilita la comprensión de conceptos como registros, memoria, instrucciones de máquina, y el ciclo de instrucción.

-   **Desarrollo de software**: Se puede utilizar para desarrollar pequeños programas en ensamblador MIPS, especialmente para aplicaciones
    embebidas donde se requiere un alto nivel de control sobre el hardware.

> [!IMPORTANT]
> Los requisitos para poder continuar con este contenido son: Vscode y las extensiones de "MARS MIPS Support for VSCode"

A partir de ahora se entrará en contenido de ensamblador MIPS32, y se harán ejercicios para practicar.

# TABLA DE CONTENIDOS

1. [Registros](#registros)
    - [Características Principales](#características-principales)
    - [Tipos de Registros](#tipos-de-registros)
        - [Registros de Propósito General](#registros-de-propósito-general)
        - [Registros de Propósito Especifico](#registros-de-propósito-específico)
    - [Porque son importantes](#porque-son-importantes)

## Registros

Los Registros en Assembly MIPS 32 Los registros en Assembly MIPS 32 son como pequeñas cajas de memoria dentro del procesador. Sirven para
almacenar temporalmente datos que se están utilizando en las operaciones del programa. Imagina que son calculadoras pequeñas y rápidas donde
el procesador realiza sus cálculos.

### Características Principales:

-   **Tamaño Fijo**: Cada registro tiene un tamaño fijo de 32 bits (4 bytes).

-   **Acceso Rápido**: El acceso a los datos almacenados en los registros es mucho más rápido que el acceso a la memoria principal.

-   **Propósito General**: La mayoría de los registros pueden utilizarse para almacenar cualquier tipo de dato (enteros, direcciones de
    memoria, etc.).

-   **Limitados**: La cantidad de registros es limitada, por lo que hay que gestionarlos de manera eficiente.

### Tipos de Registros:

1. #### Registros de Propósito General

    - **$s0 - $s7**: Estos registros suelen utilizarse para almacenar valores que deben persistir entre llamadas a funciones. Por ejemplo,
      si tienes una variable que necesita mantener su valor a lo largo de varias partes de tu programa, es común asignarla a uno de estos
      registros.
    - **$t0 - $t9**: Son registros temporales que se usan para realizar cálculos intermedios. Su contenido puede ser sobreescrito en
      cualquier momento, por lo que no son ideales para almacenar valores que necesites conservar a largo plazo.

2. #### Registros de Propósito Específico

    - **$zero**: Este registro siempre contiene el valor cero. Es útil cuando necesitas realizar operaciones que involucren el número cero,
      como por ejemplo, inicializar un registro.

    - **$a0 - $a3**: Se utilizan para pasar argumentos a las funciones. Cuando llamas a una función, los valores que deseas pasar se colocan
      en estos registros antes de realizar la llamada.

    - **$v0 - $v1**: Se emplean para devolver valores de las funciones. Al finalizar una función, el valor que se desea retornar se coloca
      en uno de estos registros.

    - **$gp**: Es el registro de apuntador global, utilizado para direccionar datos globales.

    - **$fp**: Es el registro de marco de pila, que apunta al inicio del marco de pila actual.

    - **$sp**: Es el registro de apuntador de pila, que apunta a la cima de la pila. La pila se utiliza para almacenar información local de
      las funciones, como variables locales y parámetros.

    - **$ra**: Contiene la dirección de retorno de una función. Cuando se llama a una función, la dirección de la siguiente instrucción a
      ejecutar se guarda en este registro para poder volver a ese punto una vez que la función haya terminado.

    - **$at**: Es un registro temporal utilizado por el ensamblador. No se recomienda utilizarlo directamente en el código.

### Porque son importantes

-   **Velocidad**: Al utilizar registros, se evitan las operaciones de acceso a memoria, lo que agiliza la ejecución del programa.

-   **Flexibilidad**: Permiten realizar cálculos complejos y manipular datos de manera eficiente.

-   **Optimización**: Un buen uso de los registros es clave para optimizar el código y mejorar su rendimiento.

## Instrucciones Fundamentales

Las instrucciones fundamentales en MIPS32 son como los ladrillos con los que construimos cualquier programa. Son operaciones básicas que el
procesador puede realizar directamente y que se combinan para formar programas más complejos.

1. ### Operaciones Aritméticas

    - **Suma**: La instrucción `add` se utiliza para realizar la suma de dos números enteros y almacenar el resultado en un tercer registro.
      Su formato general es el siguiente:

        ```MIPS 
            add $t1, $t2, $t3 # $t1 ←- $t2 + $t3
        ```

    - **Resta**: La instrucción `sub` se utiliza para realizar la resta de dos números enteros y almacenar el resultado en un tercer
      registro. Su formato general es el siguiente:

        ```MIPS
            sub $t1, $t2, $t3 # $t1 ←- $t2 - $t3
        ```

    - **Suma Inmediata**: La instrucción `addi` se utiliza para realizar la suma de un registro y un valor inmediato (una constante pequeña)
      y almacenar el resultado en un tercer registro. Su formato general es el siguiente:

        ```MIPS
            addi $t1, $t2, 100 # $t1 ←- $t2 + 100
        ```

2. ### Transferencia de Datos

    - **Cargar Palabra**: La instrucción `lw` (load word) nos permite bajar datos desde la memoria principal hacia un registro. Su formato
      general es el siguiente:

        ```MIPS
            lw $t0, 100($t1) # $t0 ←- memoria[$t1 + 100]
        ```

        - <ins>Explicación del codigo</ins>: Se toma la dirección del registro `$t1` y se le suma 100 de esta forma se obtiene la dirección
          de memoria que se quiere leer. Y el valor en esa dirección se almacena en el registro `$t0`.

    - **Guardar Palabra**: La instrucción `sw` (save word) nos permite guardar datos en la memoria principal desde un registro. Su formato
      general es el siguiente:

        ```MIPS
            sw $t0, 100($t1) # $memoria[$t1 + 100] ←- $t0
        ```

        - <ins>Explicación del codigo</ins>: Se toma el valor del registro `$t0` y se guarda en la dirección de memoria que se obtiene de
          sumarle a la dirección de memoria de `$t1` la constante de 100.
          
    ***
   
    - **Cargar Mitad**: La instrucción `lh` (load half) nos permite bajar datos desde la memoria principal hacia un registro. Su formato
      general es el siguiente:

        ```MIPS
            lh $t0, 100($t1) # $t0 ←- memoria[$t1 + 100]
        ```

        - <ins>Explicación del codigo</ins>: Se toma la dirección del registro `$t1` y se le suma 100 de esta forma se obtiene la dirección
          de memoria que se quiere leer. Y el valor en esa dirección se almacena en el registro `$t0`.

    - **Guardar Mitad**: La instrucción `sh` (save half) nos permite guardar datos en la memoria principal desde un registro. Su formato
      general es el siguiente:

        ```MIPS
            sh $t0, 100($t1) # $memoria[$t1 + 100] ←- $t0
        ```

        - <ins>Explicación del codigo</ins>: Se toma el valor del registro `$t0` y se guarda en la dirección de memoria que se obtiene de
          sumarle a la dirección de memoria de `$t1` la constante de 100.
          
> [!NOTE]
> `sw` y `lw` cargan una palabra de 32 bits. Una palabra en MIPS32 ocupa 4 bytes. Ambas instrucciones son utiles para
> trabajar números enteros de 32 bits o direcciones de memoria.
> Por otro lado, `sh` y `lh` cargan la mitad de una palabra de 32 bits, es decir, 16 bits. Una palabra en MIPS32 ocupa 4 bytes, por lo
> tanto, estas dos instrucciones consideran 2 bytes. Ambas instrucciones son utiles para trabajar números enteros de 16 bits,
> estructuras de datos de manera eficiente y arreglos de numeros de 16 bits.
