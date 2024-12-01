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
>
> Los requisitos para poder continuar con este contenido son: Vscode y las extensiones de "MARS MIPS Support for VSCode"

A partir de ahora se entrará en contenido de ensamblador MIPS32, y se harán ejercicios para practicar.

# TABLA DE CONTENIDOS

1. [Registros](#registros)

    - [Características Principales](#características-principales)
    - [Tipos de Registros](#tipos-de-registros)
        - [Registros de Propósito General](#registros-de-propósito-general)
        - [Registros de Propósito Especifico](#registros-de-propósito-específico)
    - [Porque son importantes](#porque-son-importantes)

2. [Instrucciones Fundamentales](#instrucciones-fundamentales)

    - [Operaciones Aritméticas](#operaciones-aritméticas)
    - [Transferencia de Datos](#transferencia-de-datos)
    - [Logica](#logica)
    - [Instrucciones Adicionales](#instrucciones-adicionales)

3. [Formatos Basicos de Instrucción](#formatos-basicos-de-instrucción)

    - [Tipos de Formatos](#tipos-de-formatos)
        - [Formato R](#formato-tipo-r)
        - [Formato I](#formato-tipo-i)
        - [Formato J](#formato-tipo-j)
    - [Comparaciones entre formatos](#comparación)

4. [Estrutura de Codigo](#estrutura-de-codigo)

5. [Ejemplos de Uso](#ejemplo-de-uso)

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

1.  ### Operaciones Aritméticas

    -   **Suma**: La instrucción `add` se utiliza para realizar la suma de dos números enteros y almacenar el resultado en un tercer
        registro. Su formato general es el siguiente:

        ```MIPS
            add     $t1,    $t2,    $t3        # $t1 <== $t2 + $t3
        ```

    -   **Resta**: La instrucción `sub` se utiliza para realizar la resta de dos números enteros y almacenar el resultado en un tercer
        registro. Su formato general es el siguiente:

        ```MIPS
            sub     $t1,    $t2,    $t3        # $t1 <== $t2 - $t3
        ```

    -   **Suma Inmediata**: La instrucción `addi` se utiliza para realizar la suma de un registro y un valor inmediato (una constante
        pequeña) y almacenar el resultado en un tercer registro. Su formato general es el siguiente:

        ```MIPS
            addi    $t1,    $t2,    100        # $t1 <== $t2 + 100
        ```

---

2.  ### Transferencia de Datos

    -   **Cargar Palabra**: La instrucción `lw` (load word) nos permite bajar datos desde la memoria principal hacia un registro. Su formato
        general es el siguiente:

        ```MIPS
            lw      $t0,    100($t1)           # $t0 <== memoria[$t1 + 100]
        ```

        -   <ins>Explicación del codigo</ins>: Se toma la dirección del registro `$t1` y se le suma 100 de esta forma se obtiene la
            dirección de memoria que se quiere leer. Y el valor en esa dirección se almacena en el registro `$t0`.

    -   **Guardar Palabra**: La instrucción `sw` (store word) nos permite guardar datos en la memoria principal desde un registro. Su
        formato general es el siguiente:

        ```MIPS
            sw      $t0,    100($t1)           # $memoria[$t1 + 100] <== $t0
        ```

        -   <ins>Explicación del codigo</ins>: Se toma el valor del registro `$t0` y se guarda en la dirección de memoria que se obtiene de
            sumarle a la dirección de memoria de `$t1` la constante de 100.

        ***

    -   **Cargar Mitad**: La instrucción `lh` (load half) nos permite bajar datos desde la memoria principal hacia un registro. Su formato
        general es el siguiente:

        ```MIPS
            lh      $t0,    100($t1)           # $t0 <== memoria[$t1 + 100]
        ```

        -   <ins>Explicación del codigo</ins>: Se toma la dirección del registro `$t1` y se le suma 100 de esta forma se obtiene la
            dirección de memoria que se quiere leer. Y el valor en esa dirección se almacena en el registro `$t0`.

    -   **Guardar Mitad**: La instrucción `sh` (store half) nos permite guardar datos en la memoria principal desde un registro. Su formato
        general es el siguiente:

        ```MIPS
            sh      $t0,    100($t1)           # $memoria[$t1 + 100] <== $t0
        ```

        -   <ins>Explicación del codigo</ins>: Se toma el valor del registro `$t0` y se guarda en la dirección de memoria que se obtiene de
            sumarle a la dirección de memoria de `$t1` la constante de 100.

        ***

    -   **Cargar Byte**: La instrucción `lb` (load byte) nos permite bajar datos desde la memoria principal hacia un registro. Su formato
        general es el siguiente:

        ```MIPS
            lb      $t0,    100($t1)           # $t0 <== memoria[$t1 + 100]
        ```

        -   <ins>Explicación del codigo</ins>: Se toma la dirección del registro `$t1` y se le suma 100 de esta forma se obtiene la
            dirección de memoria que se quiere leer. Y el valor en esa dirección se almacena en el registro `$t0`.

    -   **Guardar Byte**: La instrucción `sb` (store byte) nos permite guardar datos en la memoria principal desde un registro. Su formato
        general es el siguiente:

        ```MIPS
            sb      $t0,    100($t1)           # $memoria[$t1 + 100] <== $t0
        ```

        -   <ins>Explicación del codigo</ins>: Se toma el valor del registro `$t0` y se guarda en la dirección de memoria que se obtiene de
            sumarle a la dirección de memoria de `$t1` la constante de 100.

        ***

    -   **Carga Superior Inmediata**: La instrucción `lui` sirve para cargar un valor inmediato de 16 bits en la parte alta (bits 16-31) de
        un registro. Es decir, carga un valor constante en los bits más significativos de un registro, mientras que los 16 bits menos
        significativos se ponen a cero: Su formato general es el siguiente:

        ```MIPS
            lui     $t0,    100
        ```

        -   <ins>Explicación del codigo paso a paso</ins>:

            1. Conversión a Binario: Antes de ver cómo se carga el valor en el registro, convirtamos el inmediato 100 a binario de 16 bits
               (ya que `lui` solo carga 16 bits):

                - 100 en decimal equivale a 0x64 en hexadecimal
                - 0x64 en binario es: 01100100, (recordar que se toma el binario en 16 bits)

            2. Carga en el Registro: `lui` tomará los 16 bits del inmediato (100) y los coloca en los 16 bits más significativos del
               registro (los primeros 16 de izquierda a derecha) y los bits restantes quedaran en 0.

                - Por lo tanto, el registro `$t0` quedará con el valor: 0000000001100100 - 0000000000000000

    > [!NOTE]
    >
    > -   `sw` y `lw` cargan una palabra de 32 bits. Una palabra en MIPS32 ocupa 4 bytes. Ambas instrucciones son utiles para trabajar
    >     números enteros de 32 bits o direcciones de memoria.
    >
    > -   `sh` y `lh` cargan la mitad de una palabra de 32 bits, es decir, 16 bits. Una palabra en MIPS32 ocupa 4 bytes, por lo tanto, estas
    >     dos instrucciones consideran 2 bytes. Ambas instrucciones son utiles para trabajar números enteros de 16 bits, estructuras de
    >     datos de manera eficiente y arreglos de numeros de 16 bits.
    >
    > -   `sb` y `lb` cargan un byte de 8 bits. Son utiles para manipular datos a nivel de byte
    >
    > -   `lui` tiene como función principal cargar un valor inmediato en la parte alta de un registro. Esto significa que toma un número de
    >     16 bits y lo coloca directamente en los 16 bits más significativos (los mayores) de un registro, mientras que los 16 bits menos
    >     significativos se ponen a cero.

---

3.  ### Logica

    Asumamos lo siguiente:

    ```MIPS
    	$s0     =,      4                  # 4 => 00000100
	    $s1     =,      3                  # 3 => 00000011
    ```

    -   **AND**: Realiza una operación lógica bit a bit entre dos operandos. Es decir, compara cada bit correspondiente de ambos operandos y
        si ambos bits son 1, el bit resultante también será 1. En caso contrario, el bit resultante será 0. Su formato general es el
        siguiente:

        ```MIPS
        	and     $s2,    $s1,    $s0        # $s2 <== $s1 & $s0
        ```

        -   <ins>Comportamiento</ins>:

            | Registro | Valor en binario | Valor decimal |
            | -------- | ---------------- | ------------- |
            | `$s0`    | 00000100         | 4             |
            | `$s1`    | 00000011         | 3             |
            | `$s2`    | 00000000         | 0             |

        ***

    -   **OR**: Realiza una operación lógica bit a bit entre dos operandos. Sin embargo, a diferencia del `AND`, en el `OR` el resultado
        será 1 si al menos uno de los bits correspondientes es 1.

        ```MIPS
        	or      $s2,    $s1,    $s0        # $s2 <== $s1 | $s0
        ```

        -   <ins>Comportamiento</ins>:

            | Registro | Valor en binario | Valor decimal |
            | -------- | ---------------- | ------------- |
            | `$s0`    | 00000100         | 4             |
            | `$s1`    | 00000011         | 3             |
            | `$s2`    | 00000111         | 7             |

        ***

    -   **NOR**: La operación `NOR` es una operación lógica bit a bit que produce el complemento de la operación `OR`. Es decir, si
        realizamos una operación OR entre dos bits y luego negamos el resultado, obtenemos el resultado de una operación `NOR`.

        ```MIPS
        	nor     $s2,    $s1,    $s0        # $s2 <== ~($s1 | $s0)
        ```

        -   <ins>Comportamiento paso a paso</ins>:

            1. Invertimos los bits de `$s1` y `$s0`:

                | Registro | Valor en binario | Valor Invertido |
                | -------- | ---------------- | --------------- |
                | `$s0`    | 00000100         | 11111011        |
                | `$s1`    | 00000011         | 11111100        |

            2. Aplicamos la operación `OR` a los valores invertidos, con la escepción que si ambos bits son 1, el resultado será 0:

                | Registro Invertido | Valor Invertido |
                | ------------------ | --------------- |
                | `$s0`              | 11111011        |
                | `$s1`              | 11111100        |
                | `Resultado`        | 00000111        |

            3. Sumamos un bit al resultado obtenido y ese valor se guarda en `$s2`:

                | Registro     | Valor en binario | Valor decimal |
                | ------------ | ---------------- | ------------- |
                | `$Resultado` | 00000111         | 7             |
                |              | 00000001         | 1             |
                | `$s2`        | 00001000         | 8             |

            4. Cabe resaltar que la operación `NOR` toma en cuenta el bit de signo por lo que el valor que se guardara en `$S2` será -8.

        ***

    -   **ANDI**: La instrucción `ANDI` es una variante de la instrucción `AND`, que te permite realizar una operación lógica `AND` entre un
        registro y un valor inmediato (constante). Esta instrucción es muy útil cuando necesitas realizar operaciones lógicas simples y
        rápidas con valores constantes.

        ```MIPS
        	andi    $s2,    $s0,    14         # $s2 <== $s0 & 14
        ```

        -   <ins>Comportamiento</ins>:

            | Registro | Valor en binario | Valor decimal |
            | -------- | ---------------- | ------------- |
            | `$s0`    | 00000100         | 4             |
            |          | 00001110         | 14            |
            | `$s2`    | 00000100         | 4             |

        ***

    -   **ORI**: Realiza una operación lógica `OR` bit a bit entre un registro y un valor inmediato. Es decir, compara cada bit
        correspondiente del registro y del valor inmediato, y si al menos uno de los bits es 1, el bit resultante será 1. En caso contrario,
        el bit resultante será 0.

        ```MIPS
        	ori     $s2,    $s0,    14         # $s2 <== $s0 & 14
        ```

        -   <ins>Comportamiento</ins>:

            | Registro | Valor en binario | Valor decimal |
            | -------- | ---------------- | ------------- |
            | `$s0`    | 00000100         | 4             |
            |          | 00001110         | 14            |
            | `$s2`    | 00001110         | 14            |

        ***

    -   **SLL**: Se utiliza para realizar un desplazamiento a la izquierda lógico sobre un registro. Esto significa que cada bit del
        registro se desplaza una cierta cantidad de posiciones hacia la izquierda, y los bits que quedan vacíos a la derecha se rellenan con
        ceros.

        ```MIPS
        	sll     $s2,    $s0,    2          # $s2 <== $s0 << 2
        ```

        -   <ins>Comportamiento</ins>:

            | Registro | Valor en binario | Valor decimal | Desplazamiento | Valor resultante |
            | -------- | ---------------- | ------------- | -------------- | ---------------- |
            | `$s0`    | 00000100         | 4             | 00010000       | 16               |

            Luego el valor que se guardará en `$s2` es 16.

            **Nota**: Pueden verlo como multiplicar el valor original de `$s0` por 2 <sup>n desplaz</sup>

        ***

    -   **SRL**: Se utiliza para realizar un desplazamiento a la derecha lógico sobre un registro. Esto significa que cada bit del registro
        se desplaza una cierta cantidad de posiciones hacia la derecha, y los bits que quedan vacíos a la izquierda se rellenan con ceros.

        ```MIPS
        	srl     $s2,    $s0,    2          # $s2 <== $s0 >> 2
        ```

        -   <ins>Comportamiento</ins>:

            | Registro | Valor en binario | Valor decimal | Desplazamiento | Valor resultante |
            | -------- | ---------------- | ------------- | -------------- | ---------------- |
            | `$s0`    | 00000100         | 4             | 00000001       | 1                |

            Luego el valor que se guardará en `$s2` es 1.

            **Nota**: Pueden verlo como dividir el valor original de `$s0` entre 2 <sup>n desplaz</sup>

        ***

    > [!WARNING]
    >
    > -   Perdida de Información: `sll` y `srl` al realizar el desplazamiento, los bits más significativos pueden salirse del registro
    >     causando una perdida de información.
    >
    > -   Confusión de signo: No tienen en cuenta el signo del número, si estas trabajando con números representados en complemento a2,
    >     pueden surgir resultados inesperados

---

4.  ### Saltos Condicionales

    Asumamos lo siguiente:

    ```MIPS
    	$s0     =,      5                  # 5 => 00000101
	    $s1     =,      3                  # 3 => 00000011
    ```

    -   **BEQ**: La instrucción `beq` (branch if equal) se utiliza para realizar un salto condicional si dos registros tienen el mismo
        valor. Su formato general es:

        ```MIPS
        	beq     $s1,    $s0,    etiqueta
        ```

        -   <ins>Comportamiento</ins>:

            ```C++
            	if($s1 == $s0){
            		goTo(etiqueta);
            	}else{
            		continue;
            	}
            ```

        ***

    -   **BNE**: La instrucción `bne` (branch if not equal) se utiliza para realizar un salto condicional si dos registros tienen distinto
        valor. Su formato general es:

        ```MIPS
        	bne     $s1,    $s0,    etiqueta
        ```

        -   <ins>Comportamiento</ins>:

            ```C++
            	if($s1 != $s0){
            		goTo(etiqueta);
            	}else{
            		continue;
            	}
            ```

    > [!NOTE]
    >
    > Las etiquetas en MIPS32 son como señales de tráfico en un programa, indican un punto específico en el código al que se puede saltar o
    > referenciar desde otras partes. Si queda alguna confusion podran consultar lo que son las etiquetas en un apartado más adelante.

    ***

    -   **SLT**: La instrucción `slt` (set on less than) se utiliza para comparar dos registros y si ambos son iguales le asigna 1 a un
        registro destino y en caso contrario asigna 0. Su formato general es:

        ```MIPS
       	    slt     $s2,    $s1,    $s0
        ```

        -   <ins>Comportamiento</ins>:

            ```C++
            	if($s1 == $s0){
            		$s2 = 1;
            	}else{
            		$s2 = 0;
            	}
            ```

        ***

    -   **SLTI**: La instrucción `slti` (set on less than inmediate) se utiliza para comparar un registro y un valor inmediato o constante,
        y si el registro es menor que la constante le asigna 1 a un registro destino y en caso contrario asigna 0. Su formato general es:

        ```MIPS
            slti    $s2,    $s0,    100
        ```

        -   <ins>Comportamiento</ins>:

            ```C++
                if($s0 < 100){
                    $s2 = 1;
                }else{
                    $s2 = 0;
                }
            ```

    > [!NOTE]
    >
    > Aunque las instrucciones `slt` y `slti` no son instrucciones de saltos condicionales, se suelen utilizar en combinación con estas
    > instrucciones para crear condiciones más complejas motivo por el cual se incluyen en este apartado. Sin embargo cabe resaltar que son
    > instrucciones de operaciones aritméticas

---

5.  ### Salto Incondicional

    -   **J**: La instrucción `j` (jump) se utiliza para saltar a una etiqueta especificada en el código. Su formato general es:

        ```MIPS
        	j       etiqueta
        ```

        -   <ins>Comportamiento</ins>: Mueve la ejecución del codigo a la etiqueta especificada. No guarda la dirección de retorno en un
            registro.

    ***

    -   **JAL**: La instrucción `jal` (jump and link) se utiliza para saltar a una etiqueta especificada en el código y guarda la dirección
        de la siguiente instrucción a ejecutar en un registro para regresar a ella. Su formato general es:

        ```MIPS
        	jal     etiqueta
        ```

        -   <ins>Comportamiento</ins>: Mueve la ejecución del codigo a la etiqueta especificada. Guarda la dirección de retorno en el
            registro `$ra` (return address).

    ***

    -   **JR**: La instrucción `jr` (jump register) se utiliza para transferir el flujo de ejecución a una dirección de memoria especificada
        por el contenido de un registro, las instrucciones `beq`, `bne` y `jal` luego de ejecutarse guardan la dirección de la siguiente
        instrucción al registro `$ra` y la instrucción `jr` se utiliza para regresar a ella. Su formato general es:

        ```MIPS
        	jr      $ra
        ```

        -   <ins>Comportamiento</ins>: Mueve la ejecución del codigo a la dirección en el registro `$ra` (return address).

---

6.  ### Instrucciones Adicionales

    -   **LA**: La instrucción `la` (load address) se utiliza para cargar la dirección de una etiqueta en un registro. Su formato general
        es:

        ```MIPS
        	la      $a0,    etiqueta
        ```

        -   <ins>Comportamiento</ins>: Carga la dirección de la etiqueta en el registro `$a0`.

    ***

    -   **MOVE**: La instrucción `move` se utiliza para copiar el contenido de un registro a otro. Su formato general es:

        ```MIPS
        	move    $t0,    $t1
        ```

        -   <ins>Comportamiento</ins>: Copia el contenido de `$t1` a `$t0`.

    ***

    -   **LI**: La instrucción `li` es una pseudoinstrucción que se utiliza para cargar un valor inmediato (es decir, un número fijo) en un
        registro. Es una forma conveniente de asignar valores a los registros sin tener que realizar cálculos complejos.

        ```MIPS
        	li      $v0,    10
        ```

        -   <ins>Comportamiento</ins>: Carga el valor 10 en el registro `$v0`.

    ***

    -   **SYSCALL**: Esta instrucción provoca que el procesador interrumpa su ejecución actual y transfiera el control al sistema operativo.
        El tipo de llamada al sistema que se realizará depende del valor que se haya cargado previamente en el registro `$v0`. Y, en este
        contexto, el registro `$v0` indica el número de la llamada al sistema que se desea realizar. Cada número corresponde a una función
        del sistema operativo (por ejemplo, imprimir un número, leer del teclado, etc.). Otros registros, como $a0, $a1, etc., pueden
        utilizarse para pasar argumentos a la llamada al sistema.

        ```MIPS
        	li      $v0,    10
	        syscall
        ```

        -   <ins>Comportamiento</ins>: Esta instrucción desencadena la ejecución de la llamada al sistema especificada por el valor en el
            registro $v0. En otras palabras, le dice al sistema operativo: "Por favor, realiza la acción correspondiente al código 10 que he
            cargado en $v0".

        -   <ins>Codigos de syscall</ins>:

            | Codigo | Descripción                       |
            | ------ | --------------------------------- |
            | 1      | Imprimir un entero                |
            | 4      | Leer un entero                    |
            | 8      | Imprimir una cadena de caracteres |
            | 9      | Leer una cadena de caracteres     |
            | 10     | Terminar el programa              |
            | 11     | Abrir un archivo                  |
            | 12     | Cerrar un archivo                 |
            | 13     | Leer de un archivo                |
            | 14     | Escribir en un archivo            |

## Formatos Basicos de Instrucción

Los formatos básicos de instrucción en MIPS 32 son fundamentales para entender cómo se estructuran y ejecutan las instrucciones en esta
arquitectura. Estos formatos definen la manera en que los diferentes campos de una instrucción (como el código de operación, los registros y
los valores inmediatos) se organizan en una palabra de 32 bits.

Los formatos de instrucción en MIPS son como un "lenguaje común" entre el programador y el procesador.

Imagina que estás dando instrucciones a un robot. Tú le dices qué hacer (sumar, restar, saltar, etc.), pero el robot necesita entender esas
instrucciones en un formato específico para poder llevarlas a cabo. Los formatos de instrucción en MIPS son ese formato específico.

### Tipos de Formatos

MIPS 32 utiliza principalmente tres formatos de instrucción: Tipo R, Tipo I y Tipo J. Cada uno de estos formatos tiene una estructura
específica y se utiliza para diferentes tipos de operaciones.

1.  #### Formato Tipo R

    -   **Características**: Utilizado para operaciones aritméticas y lógicas que involucran solo registros.

    -   **Estructura**:

        | Tamaño por campo (en bits) | cod oper | rs      | rt      | rd      | desplaz | funct |
        | -------------------------- | -------- | ------- | ------- | ------- | ------- | ----- |
        | Maximo por instrucción: 32 | 31 - 26  | 25 - 21 | 20 - 16 | 15 - 11 | 10 - 6  | 5 - 0 |

    -   **Descripción**:

        1. cod oper: Código de operación (identifica la instrucción).

        2. rs: Registro fuente 1.

        3. rt: Registro fuente 2.

        4. rd: Registro destino.

        5. desplaz: Cantidad de desplazamiento (para instrucciones de shift).

        6. funct: Código de función (especifica la operación exacta).

    -   **Ejemplo**:

        ```MIPS
            add     $a0,    $t0,    $t1
        ```

        | cod oper | rs    | rt    | rd    | desplaz | funct |
        | -------- | ----- | ----- | ----- | ------- | ----- |
        | op       | `$t0` | `$t1` | `$a0` | 0       | add   |

        Donde:

        -   `op` representa el código de operación para instrucciones tipo R.
        -   `rs` es el primer registro fuente `$t0`.
        -   `rt` es el sedundo registro fuente `$t1`.
        -   `rd` es el registro destino `$a0`, donde se almacenará el resultado de la suma.
        -   `desplaz` es 0, ya que no estamos realizando un desplazamiento.
        -   `add` es el código de función específico para la operación de suma. Por ende se pone en el campo `funct`

    ***

2.  #### Formato Tipo I

    -   **Características**: Utilizado principalmente para instrucciones que involucran una constante o un valor inmediato (de 16 bits).
        Este formato es ideal para operaciones donde necesitamos sumar o restar un valor constante a un registro, cargar o almacenar datos
        de la memoria, o realizar saltos condicionales.

    -   **Estructura**:

        | Tamaño por campo (en bits) | cod oper | rs      | rt      | imm    |
        | -------------------------- | -------- | ------- | ------- | ------ |
        | Maximo por instrucción: 32 | 31 - 26  | 25 - 21 | 20 - 16 | 15 - 0 |

    -   **Descripción**:

        1. cod oper: Código de operación (identifica la instrucción).

        2. rs: Registro fuente.

        3. rt: Registro destino o segundo registro fuente.

        4. imm: inmediato(valor constante de 16 bits) o dirección de memoria.

    -   **Ejemplo**:

        ```MIPS
            addi     $t0,    $s0,    10
        ```

        | cod oper | rs    | rt    | imm |
        | -------- | ----- | ----- | --- |
        | op_addi  | `$s0` | `$t0` | 10  |

        Donde:

        -   `op_addi` representa el código de operación `addi` para el formato tipo I.
        -   `rs` es el registro fuente `$t0`.
        -   `rt` es el segundo registro fuente o registro de destino `$s0`.
        -   `imm` es el valor inmediato de 16 bits, que es 10 en este caso.

    ***

3.  #### Formato Tipo J

    -   **Características**: Principalmente para instrucciones de salto incondicional (jump) a una dirección de memoria específica. Se usa
        para cambiar el flujo de la ejecucion del programa y para saltar a una ubicación específica en la memoria, como a un procedimiento.

    -   **Estructura**:

        | Tamaño por campo (en bits) | cod oper | address |
        | -------------------------- | -------- | ------- |
        | Maximo por instrucción: 32 | 31 - 26  | 25 - 0  |

    -   **Descripción**:

        1. cod oper: Código de operación (identifica la instrucción).

        2. address: Dirección a la que va a seguir el flujo de la ejecución.

    -   **Ejemplo**:

        ```MIPS
            jr      $ra
        ```

        | cod oper | address |
        | -------- | ------- |
        | op_jr    | `$ra`   |

        Donde:

        -   `op_jr` representa el código de operación `jr` para el formato tipo J.
        -   `address` es el registro que contiene la dirección a la que se va a saltar `$ra`.

    ***

### Comparación 

- **Comparación en Estructura**:

| Característica | Formato R                                         | Formato I                                                                        | Formato J                                      |
| -------------- | ------------------------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------- |
| Uso principal  | Operaciones aritméticas y lógicas entre registros | Acceso a memoria, operaciones aritméticas con un inmediato, saltos condicionales | Saltos incondicionales a direcciones distantes |
| Estructura     | cod oper, rs, rt, rd, desplaz, funct              | cod oper, rs, rt, imm                                                            | cod oper, address                              |

- **Comparación en Campos**:

| Campos                    |                                     |                                            |                                     |
| ------------------------- | ----------------------------------- | ------------------------------------------ | ----------------------------------- |
| cod oper                  | Codigo de operación para el formato | Codigo de operación para el formato        | Codigo de operación para el formato |
| rs                        | Registro fuente 1                   | Registro fuente                            | **No aplica**                       |
| rt                        | Registro fuente 2                   | Segundo Registro fuente o registro destino | **No aplica**                       |
| rd                        | Registro destino                    | **No aplica**                              | **No aplica**                       |
| desplaz                   | Cantidad de desplazamiento (shift)  | **No aplica**                              | **No aplica**                       |
| funct                     | Codigo de funcion                   | Registro fuente                            | **No aplica**                       |
| imm                       | **No aplica**                       | Valor inmediato o dirección                | **No aplica**                       |
| address                   | **No aplica**                       | **No aplica**                              | Dirección de memoria o etiqueta     |
| Ejemplos de instrucciones | `add, sub, and, or, sll, srl`       | `lw, sw, addi, beq, bne`                   | `j, jal, jr`                        |

> [!WARNING]
>
> No confundir los formatos basicos de instrucción con la sintaxis de la instrucción en mips. Los formatos de instrucción son la forma en la
> que mips procesa las instrucciones, la sintaxis es de una forma y la forma de los formatos de instrucción es otra para la interpretacion
> del procesador

## Estrutura de Codigo

Para este ejemplo mostraremos un programa que imprime en consola "Hello world" en mips de modo que se ira desglosando sus instrucciones paso
a paso

-   **Ejemplo**:

    ```MIPS
        .data
        mss:    .asciiz "Hello world!\n"

        .text
                .globl  main

        main:

	        li      $v0,    4
	        la      $a0,    mss
	        syscall

	        li      $v0,    10
	        syscall
    ```

    1. **Sección data**:

        - `.data`:Esta directiva le indica al ensamblador que a partir de este punto se definirán los datos. Es decir, se reservará un
          espacio en la memoria para almacenar variables, constantes y cadenas de texto.

        - `mss: .asciiz "Hello world!\n"`: Aquí se define una cadena de texto llamada "mensaje". La directiva `.asciiz` indica que se trata
          de una cadena terminada en null (un carácter especial que marca el final de la cadena).

    2. **Sección text**:

        - `.text`: Esta directiva señala el inicio de la sección de código, donde se escribirán las instrucciones que el procesador
          ejecutará.

        - `.global main`: Esta directiva declara que la etiqueta `main` es global, lo que significa que puede ser referenciada desde otros
          archivos o módulos. En este caso, `main` es el punto de entrada del programa, es decir, la primera instrucción que se ejecutará.

    3. **Etiqueta main**:

        - `main:`: Esta etiqueta marca el inicio de la función principal del programa. Todas las instrucciones que se escriban a
          continuación de esta etiqueta pertenecerán a la función main.

> [!NOTE]
>
> **Las etiquetas en MIPS 32**: Sirven para marcar puntos específicos del código a los que podemos saltar o referenciar desde otras partes.
> Imaginemos un mapa: las etiquetas son como las ciudades o pueblos que queremos visitar. En lugar de usar coordenadas exactas (direcciones
> de memoria), usamos nombres fáciles de recordar (etiquetas) para indicar nuestro destino. Esto hace que nuestro código sea más legible,
> mantenible y fácil de entender, tanto para nosotros como para otros programadores.

## Ejemplo de Uso

Aqui nada más se hara un ejemplo de uso basico en conversion de un codigo en lenguaje `C` y luego en `MIPS`, dentro del respositorio podran
encontrar ejemplos de algoritmos mas complejos y explicados en la logica de su conversion.

-   **Lenguaje C**:

    ```C
        int ejemplo_hoja(int g, int h, int i, int j){
            int f;

            f = ( g + h ) - ( i + j );

            return f;
        }

    ```

    -   **<ins>Explicación del Codigo</ins>**: Esta función recibe cuatro parámetros: `g`, `h`, `i` y `j`, todos enteros. Posteriormente
        declara una variable `f` en la cual se guardará el resultado de operar los parámetros recibidos para luego regresar ese resultado

-   **MIPS**:

    Para nosotros poder convertir el codigo anterior a MIPS, debemos tener en cuenta las siguientes reglas:

    -   **Variables**: En mips usamos registros para almacenar valores de la misma manera que en C usamos variables. Sin embargo , en MIPS
        no hace falta declararlos antes de usarlos ya que siempre estan disponibles para su uso

    -   **Parametros**: Usaremos los registros determinados de entrata (`$a0 - $a3`) para almacenar los valores de los parámetros del
        procedimiento.

    -   **Reserva de espacio**: Primero hay que reservar el espacio en la pila para luego almacenar el valor de los registros temporales que
        vamos a usar para realizar las operaciones. Esto debido a que a nivel del procedimiento no deberiamos poder cambiar el valor que
        habia previamente en esos registros.

    -   **Operaciones**: Usaremos instrucciones para realizar las operaciones aritmeticas y para guardar el valor del resultado en el
        registro determinado para la salida del procedimiento

    -   **Liberar memoria**: Después de usar los registros temporales, debemos restaurar el valor que tenian antes de entrar al
        procedimiento. Y luego liberamos el espacio en la pila que habiamos reservado.

    -   **Retorno**: Una vez puesto el resultado en el registro de returno y haber liberado la memoria, podemos proceder a enviar el flujo
        de ejecucion devuelta a la etiqueta que llamo al procedimiento

    ```MIPS
        .data
        .text

        ejemplo_hoja:

	        addi    $sp,    $sp,    -12    # Reservamos espacio en la pila

	        # Guardamos los valores de los registros temporales
	        sw      $t0,    8($sp)
	        sw      $t1,    4($sp)
	        sw      $s0,    0($sp)

	        # Realizamos las operaciones referentes a la suma y guardamos los resultados en los registros temporales
	        add     $t0,    $a0,    $a1
	        add     $t1,    $a2,    $a3

	        sub     $s0,    $t0,    $t1    # Realizamos la operación de resta y guardamos el resultado en el registro temporal

	        add     $v0,    $s0,    $zero  # Movemos el resultado de las operaciones al registro de salida

	        # Se restaura el valor de los registros temporales a su valor original antes de entrar en el procedimiento
	        lw      $t0,    8($sp)
	        lw      $t1,    4($sp)
	        lw      $s0,    0($sp)

	        addi    $sp,    $sp,    12     # Liberamos el espacio en la pila

	        jr      $ra                    # Se regresa el flujo de ejecución a la etiqueta que llamo al procedimiento
    ```
