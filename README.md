# Assembly Personal Documentation
> By Miguelangel Vasquez

## Assembly

### Que es ??

Es un lenguaje de programación de bajo nivel que utiliza mnemónicos para representar las instrucciones que se ejecutarán directamente en el
procesador. Cada instrucción en ensamblador corresponde a una operación específica del hardware, como sumar números, mover datos en la
memoria o saltar a otra parte del código.

### Características

-   <ins>Muy cercano al hardware</ins> : Permite un control muy preciso sobre el funcionamiento del procesador y otros componentes.
    Dependiente de la arquitectura: Cada tipo de procesador (x86, ARM, etc.) tiene su propio lenguaje ensamblador. Dificultad: Es
    considerado un lenguaje de programación difícil de aprender y utilizar debido a su bajo nivel de abstracción y la necesidad de conocer a
    fondo la arquitectura del procesador.

-   <ins>Dependiente de la arquitectura</ins> : Cada tipo de procesador (x86, ARM, etc.) tiene su propio lenguaje ensamblador.

-   <ins>Dificultad</ins> : Es considerado un lenguaje de programación difícil de aprender y utilizar debido a su bajo nivel de abstracción
    y la necesidad de conocer a fondo la arquitectura del procesador.

> [!NOTE]
> El Assembly que se usara a continuación es el de MIPS 32, y se usara una extensión de vscode, "MARS MIPS Support for vscode", para su ejecución

Los Registros en Assembly MIPS 32 Los registros en Assembly MIPS 32 son como pequeñas cajas de memoria dentro del procesador. Sirven para
almacenar temporalmente datos que se están utilizando en las operaciones del programa. Imagina que son calculadoras pequeñas y rápidas donde
el procesador realiza sus cálculos.

Características Principales: Tamaño Fijo: Cada registro tiene un tamaño fijo de 32 bits (4 bytes). Acceso Rápido: El acceso a los datos
almacenados en los registros es mucho más rápido que el acceso a la memoria principal. Propósito General: La mayoría de los registros pueden
utilizarse para almacenar cualquier tipo de dato (enteros, direcciones de memoria, etc.). Limitados: La cantidad de registros es limitada,
por lo que hay que gestionarlos de manera eficiente. Tipos de Registros: Registros de Propósito General

$s0 - $s7: Estos registros suelen utilizarse para almacenar valores que deben persistir entre llamadas a funciones. Por ejemplo, si tienes una variable que necesita mantener su valor a lo largo de varias partes de tu programa, es común asignarla a uno de estos registros.
$t0 -
$t9: Son registros temporales que se usan para realizar cálculos intermedios. Su contenido puede ser sobreescrito en cualquier momento, por
lo que no son ideales para almacenar valores que necesites conservar a largo plazo. Registros con Propósito Específico

$zero: Este registro siempre contiene el valor cero. Es útil cuando necesitas realizar operaciones que involucren el número cero, como por ejemplo, inicializar un registro.
$a0 -
$a3: Se utilizan para pasar argumentos a las funciones. Cuando llamas a una función, los valores que deseas pasar se colocan en estos registros antes de realizar la llamada.
$v0 -
$v1: Se emplean para devolver valores de las funciones. Al finalizar una función, el valor que se desea retornar se coloca en uno de estos registros.
$gp:
Es el registro de apuntador global, utilizado para direccionar datos globales.
$fp: Es el registro de marco de pila, que apunta al inicio del marco de pila actual.
$sp: Es el registro de apuntador de pila, que apunta a
la cima de la pila. La pila se utiliza para almacenar información local de las funciones, como variables locales y parámetros.
$ra: Contiene la dirección de retorno de una función. Cuando se llama a una función, la dirección de la siguiente instrucción a ejecutar se guarda en este registro para poder volver a ese punto una vez que la función haya terminado.
$at:
Es un registro temporal utilizado por el ensamblador. No se recomienda utilizarlo directamente en el código. ¿Por qué son importantes?
Velocidad: Al utilizar registros, se evitan las operaciones de acceso a memoria, lo que agiliza la ejecución del programa. Flexibilidad:
Permiten realizar cálculos complejos y manipular datos de manera eficiente. Optimización: Un buen uso de los registros es clave para
optimizar el código y mejorar su rendimiento.
