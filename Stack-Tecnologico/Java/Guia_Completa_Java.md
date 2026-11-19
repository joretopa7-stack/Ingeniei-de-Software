# JAVA

**Guía completa de programación Java: desde los fundamentos hasta prácticas avanzadas**  
**Versión didáctica recomendada:** Java SE 25 (JDK 25), LTS según Oracle.  
**Última versión GA identificada al 18 de noviembre de 2026:** Java SE / JDK 27, disponible desde el 15 de septiembre de 2026.  
**Fecha de corte:** 18 de noviembre de 2026.

[![Logotipo oficial de afinidad «I code Java»](https://dev.java/assets/images/java-affinity-logo-icode-lg.png)](https://dev.java/)

> Este emblema oficial de afinidad se conserva intacto y enlaza activamente a dev.java, de acuerdo con las condiciones de Oracle [1]. Esta guía es material educativo independiente y no implica patrocinio ni afiliación de Oracle. La imagen se carga desde un recurso externo; su visualización depende del visor Markdown.

Java es un lenguaje de propósito general que se compila a bytecode para la JVM y se apoya en especificaciones y APIs de plataforma. **Java SE** define el lenguaje, la máquina virtual y bibliotecas de plataforma; **JDK** es el kit de desarrollo de un proveedor que incorpora compilador, herramientas y runtime para construir y ejecutar aplicaciones. OpenJDK es el proyecto de referencia abierto; Oracle JDK, Eclipse Temurin y otras distribuciones son productos/compilaciones de proveedores con políticas de licencias, actualizaciones y soporte propias. Verifica las condiciones de la distribución elegida antes de desplegar [2][3][4].

**Por qué aprender con Java 25:** es la LTS más reciente indicada por la hoja de ruta de Oracle al corte y ofrece una base estable para cursos, proyectos y dependencias que aún no hayan validado Java 27. Java 27 es la GA de características más reciente, pero Oracle la clasifica como no LTS. La etiqueta y el calendario de soporte dependen de cada proveedor; la hoja de ruta de Oracle prevé Java 29 como siguiente LTS en septiembre de 2027, pero es una previsión, no una versión ya disponible. Para compatibilidad, escribe en Java 25 y fija `--release 25`/toolchain cuando proceda; adopta 27 si necesitas sus novedades y tu proveedor, plataforma, bibliotecas y despliegue lo admiten. Una aplicación Java 25 no necesariamente puede usar un runtime anterior a 25, y compilar con un JDK más nuevo no cambia por sí solo la compatibilidad de APIs [5][3][6].

**Alcance y cautela sobre ejemplos:** los 16 temas siguen la guía general adjunta. El cuerpo integra conceptos de Java SE y marca bibliotecas externas donde corresponde. Salidas y comandos son ejemplos esperados/ilustrativos, no prueba de ejecución en todos los sistemas. Las características *preview* o *incubator* se identifican como tales y no son base de código portable para principiantes. Cuando se cita una herramienta o framework de terceros, consulta su propia versión, licencia y compatibilidad. La biblioteca estándar no requiere instalación separada; las dependencias externas sí [7][8].

## Índice

1. [Fundamentos y características del lenguaje Java](#1-fundamentos-y-características-del-lenguaje-java)
2. [Sintaxis y semántica](#2-sintaxis-y-semántica)
3. [Tipos de datos y sistema de tipos](#3-tipos-de-datos-y-sistema-de-tipos)
4. [Fundamentos de programación](#4-fundamentos-de-programación)
5. [Estructuras de datos](#5-estructuras-de-datos)
6. [Paradigmas de programación](#6-paradigmas-de-programación)
7. [Modularidad y organización del código](#7-modularidad-y-organización-del-código)
8. [Memoria, objetos y gestión de recursos](#8-memoria-objetos-y-gestión-de-recursos)
9. [Entrada, salida y serialización](#9-entrada-salida-y-serialización)
10. [Concurrencia y paralelismo](#10-concurrencia-y-paralelismo)
11. [Manejo de errores y depuración](#11-manejo-de-errores-y-depuración)
12. [Seguridad en Java](#12-seguridad-en-java)
13. [Instalación, herramientas y ciclo de desarrollo](#13-instalación-herramientas-y-ciclo-de-desarrollo)
14. [Pruebas de software](#14-pruebas-de-software)
15. [Ecosistema y bibliotecas](#15-ecosistema-y-bibliotecas)
16. [Buenas prácticas y calidad del código](#16-buenas-prácticas-y-calidad-del-código)
17. [Aplicabilidad entre lenguajes](#17-aplicabilidad-entre-lenguajes)
18. [Ruta pedagógica para estudiar Java](#18-ruta-pedagógica-para-estudiar-java)
19. [Referencia rápida](#19-referencia-rápida)
20. [Errores frecuentes](#20-errores-frecuentes)
21. [Ejercicios progresivos](#21-ejercicios-progresivos)
22. [Soluciones](#22-soluciones)
23. [Mini proyectos](#23-mini-proyectos)
24. [Glosario](#24-glosario)
25. [Referencias](#25-referencias)

## 1. Fundamentos y características del lenguaje Java

### Qué es Java

Java es un lenguaje de programación de propósito general, concurrente, basado en clases y orientado a objetos. Su especificación actual también lo caracteriza como fuertemente y estáticamente tipado. Está pensado para programas de producción y su diseño procura que las mismas construcciones del lenguaje tengan significado consistente entre implementaciones conformes [10].

En el habla cotidiana, «Java» puede referirse al lenguaje, a la plataforma Java SE o a una instalación de desarrollo. Conviene separar esos sentidos. El lenguaje define la sintaxis y la semántica del código fuente; Java SE define una plataforma estándar, sus bibliotecas centrales y contratos; un JDK es una implementación distribuible con herramientas para desarrollar y ejecutar programas. Un producto descargable como Oracle JDK o Eclipse Temurin es una distribución/build concreta de esa plataforma, con su propio proveedor, empaquetado, calendario de actualizaciones, soporte y términos de uso [10] [3] [11] [12].

El propósito temprano de Java fue posibilitar software para dispositivos electrónicos de consumo con arquitecturas diversas. Su equipo lo reorientó después al software conectado a redes e Internet. De ahí procede el objetivo de portabilidad asociado a la frase «escribir una vez, ejecutar en distintos entornos»: se compila normalmente a bytecode para la JVM, y una implementación de JVM compatible ejecuta ese bytecode en un sistema concreto. La portabilidad es una meta del diseño, no una promesa de que cualquier programa funcionará sin cambios en cualquier máquina: también intervienen la versión objetivo, APIs disponibles, dependencias, sistema operativo, configuración, codificaciones, bibliotecas nativas y comportamiento del proveedor [10] [13].

#### Java, Java SE, JDK, JRE y JVM

| Término | Qué significa | Para qué sirve |
|---|---|---|
| **Java** | El lenguaje y, por extensión coloquial, la plataforma o el ecosistema. | Escribir programas; hay que precisar el sentido cuando se habla de instalación o compatibilidad. |
| **Java SE** | Java Platform, Standard Edition: especificaciones del lenguaje, la máquina virtual y APIs estándar para aplicaciones generales. | Define contratos con los que las implementaciones compatibles deben interoperar. No es sinónimo de una licencia ni de una compilación de proveedor. |
| **JDK** | *Java Development Kit*: kit que normalmente proporciona runtime y herramientas, por ejemplo `java`, `javac`, `jar`, `javadoc` y herramientas de diagnóstico. | Es la opción habitual para programar, compilar, probar y ejecutar. El contenido exacto varía según proveedor y empaquetado. |
| **JRE** | *Java Runtime Environment*: nombre histórico para el entorno que permite ejecutar aplicaciones Java, con JVM, bibliotecas y archivos necesarios. | Distingue conceptualmente el conjunto de ejecución del kit de desarrollo. No debe suponerse que las versiones modernas se distribuyan como una descarga separada llamada «JRE». |
| **JVM** | *Java Virtual Machine*: máquina abstracta especificada que carga, enlaza y ejecuta bytecode de archivos de clase. | Define el entorno de ejecución compatible. HotSpot es una implementación de JVM popular, no otro nombre para la especificación JVM. |

La descripción tradicional de JRE como subconjunto del JDK resulta útil para entender los términos, pero no describe necesariamente la forma en que hoy se instala Java. Desde Java 9, el JDK se organiza como imagen de ejecución modular; la especificación de OpenJDK explica que una imagen JDK es una imagen de runtime que además incluye el conjunto completo de herramientas de desarrollo. También existe `jlink`, que permite ensamblar imágenes de ejecución personalizadas con módulos seleccionados. Por ello, una instalación actual puede contener runtime y herramientas en una misma imagen sin ofrecer un JRE genérico separado [14] [15].

La JVM tampoco es un compilador único ni una aplicación idéntica en todas partes. `javac` suele traducir el fuente `.java` a archivos `.class` con bytecode; el lanzador `java` inicia el runtime y la JVM; la implementación puede interpretar bytecode, compilar partes a código máquina durante la ejecución y optimizar dinámicamente. Esas estrategias y sus efectos en consumo, arranque y rendimiento dependen de la JVM, sus opciones y el sistema operativo [10] [16].

**Distinción importante sobre estándar y proveedor:** Java SE es la plataforma/especificación; Oracle JDK, Eclipse Temurin y otras builds son productos o distribuciones que implementan componentes Java. La certificación de compatibilidad, los ciclos de actualizaciones, el periodo de soporte, los binarios incluidos y la licencia deben comprobarse para la build concreta. Por ejemplo, Adoptium declara que Temurin pasa el Java Compatibility Kit y ofrece sus binarios bajo GPLv2 con Classpath Exception; Oracle publica términos específicos para Oracle JDK, distintos de los de otros proveedores. No se puede deducir la licencia de todas las distribuciones a partir de la palabra «Java» o de la especificación Java SE [11] [12].

**Errores frecuentes al hablar de la plataforma:**

- Decir «instalé Java» sin precisar si se instaló un JDK o un runtime y de qué proveedor.
- Llamar JVM al JDK completo. La JVM ejecuta bytecode; el JDK incluye herramientas adicionales.
- Suponer que «JRE» es siempre una descarga oficial separada disponible para toda versión. El concepto sigue siendo útil, pero los empaquetados modernos difieren.
- Confundir compatibilidad con licencia gratuita, soporte comercial o actualizaciones de seguridad. Son cuestiones distintas y específicas del proveedor.
- Asumir que cualquier bytecode funciona con cualquier JVM y versión. La versión de bytecode, APIs y dependencias impone límites de compatibilidad.

**Recomendación profesional:** al documentar o fijar Java, anota como mínimo la versión de Java SE/JDK, el proveedor o distribución, la arquitectura y sistema operativo objetivo, el modo de distribución y las condiciones de soporte/licencia aplicables. En sistemas empresariales, también deja explícita la política de actualizaciones de seguridad y el nivel de compatibilidad requerido.

### Historia y evolución

Java nació en el Green Project de Sun Microsystems, iniciado en 1991 para explorar software para electrónica de consumo. El lenguaje se llamó inicialmente **Oak** y James Gosling fue su diseñador principal. A medida que el equipo revisó su objetivo, lo reorientó a redes e Internet y lo renombró Java. La especificación histórica describe expresamente ese origen, así como la intención de crear un lenguaje concurrente, orientado a objetos, de propósito general y con pocas dependencias de implementación [13] [17].

| Hito | Importancia |
|---|---|
| **1991: Green Project y Oak** | Inicio del proyecto de electrónica de consumo. El bytecode y la máquina virtual respondían a la necesidad de ejecutar software en equipos diferentes. |
| **1995–1996: anuncio y Java 1.0** | Java se presentó públicamente en 1995 y su versión 1.0 llegó a disponibilidad general en enero de 1996. La difusión de Internet dio visibilidad a su portabilidad y capacidades de red [17] [18]. |
| **1998: Java 2 / J2SE 1.2** | La plataforma se consolidó como una plataforma general con un conjunto mayor de APIs y bibliotecas. «Java 2» fue una denominación de producto histórica; hoy se habla de Java SE y de su versión [19]. |
| **2004: Java 5** | Introdujo cambios de lenguaje importantes como genéricos, tipos enumerados, anotaciones, autoboxing y bucle mejorado. Desde Java 5 se omitió el «1.» en la denominación comercial: el lanzamiento se llamó Java 5, aunque internamente se identificara como 1.5 [19]. |
| **2014: Java 8** | Incorporó expresiones lambda y características relacionadas, facilitando un estilo funcional para operar con colecciones, sin convertir Java en un lenguaje funcional puro [20]. |
| **2017: Java 9** | Incorporó el Java Platform Module System. El sistema de módulos permite expresar dependencias y encapsulación entre componentes de la plataforma y aplicaciones; también cambió la estructura interna de imágenes de runtime [15] [21]. |
| **Desde Java 10 / 2018: cadencia semestral** | El modelo moderno planifica versiones de características aproximadamente cada seis meses, una en marzo y otra en septiembre. Esto hace que nuevas capacidades lleguen en incrementos más frecuentes; requiere distinguir versiones de características de versiones de actualización [18] [22]. |
| **Java 25 y Java 27** | Java 25 fue publicada en septiembre de 2025 y es la LTS más reciente al corte. Java 27 llegó a GA el 15 de septiembre de 2026 y es la versión más reciente disponible, pero no es LTS [18] [3]. |

La evolución no consiste en reemplazar el lenguaje cada pocos años. El proceso de Java incorpora especificaciones, propuestas JEP, implementaciones y revisiones de compatibilidad. Las funciones nuevas pueden pasar por estados de *preview* o *incubator* antes de convertirse en características permanentes. Una función preview requiere habilitación explícita y no debe presentarse como API estable. Antes de adoptarla en material de estudio o software mantenido, comprueba su estado en la documentación de la versión correspondiente [10] [23].

### Versiones, cadencia y LTS

**GA** (*General Availability*, disponibilidad general) indica que una versión ya se publicó como lanzamiento final, a diferencia de una compilación de acceso anticipado. **LTS** (*Long-Term Support*) describe una designación y una oferta de mantenimiento extendido de un proveedor; no es una propiedad universal que la especificación Java SE imponga a todas las implementaciones. El calendario y la duración del soporte pueden variar entre Oracle, Adoptium y otros proveedores [18] [3] [12].

Al **18 de noviembre de 2026**, la información oficial consultada confirma lo siguiente:

- **Última versión GA:** JDK 27, GA el **15 de septiembre de 2026**. JDK 28 está en desarrollo, por tanto no es GA a esta fecha [18] [19].
- **LTS más reciente según Oracle:** Java SE/JDK 25, GA el **16 de septiembre de 2025**. La hoja de ruta de Oracle identifica como LTS Java 8, 11, 17, 21 y 25; identifica JDK 26 y 27 como no LTS. Oracle indica que planea Java 29 para septiembre de 2027 como siguiente LTS, pero esa fecha es futura y planificada, no un lanzamiento ya disponible [3].
- **Cadencia de características:** una nueva versión de características cada seis meses, según el modelo de OpenJDK; las fechas observadas se ubican en marzo y septiembre [18] [22].

| Estado al corte | Versión | Qué significa para quien estudia |
|---|---:|---|
| GA más reciente | **27** | Incluye el conjunto más nuevo de funciones finalizadas para esa versión; no implica el mayor periodo de soporte ni que todas las dependencias ya la adopten. |
| LTS más reciente | **25** | Base más conservadora para estudiar y construir aplicaciones de ciclo largo cuando el proveedor elegido la mantiene. |
| Siguiente LTS planificada por Oracle | **29, septiembre de 2027** | Es una expectativa del roadmap de Oracle; no debe tratarse como versión actual ni como garantía para todos los proveedores. |

#### Versión objetivo recomendada para esta guía

Se recomienda **Java SE 25 LTS como línea base didáctica**, con un **JDK 25 mantenido por el proveedor que elija el proyecto**. Es la LTS más reciente al corte y permite estudiar una plataforma actual sin perseguir cada lanzamiento semestral. Las construcciones básicas de los ejemplos de esta sección son compatibles con versiones anteriores y no dependen de funciones preview. Para proyectos que necesiten usar Java 27, se debe validar la compatibilidad de bibliotecas, sistemas de compilación, IDE, runtime de producción y soporte de proveedor antes de actualizar.

La recomendación no equivale a afirmar que Java 25 tenga idéntica disponibilidad, soporte o licencia en todas las distribuciones. Por ejemplo, la página de Oracle describe los términos y periodos de Oracle JDK; Adoptium ofrece Temurin con sus propios términos y políticas. Para despliegues, lee las condiciones de la distribución específica y registra cómo recibirás las actualizaciones [3] [11] [12].

### Paradigmas que admite Java

Un **paradigma** es una manera de organizar el razonamiento y la estructura de un programa. Los paradigmas no son siempre opciones excluyentes: una aplicación Java puede combinar objetos, métodos imperativos, funciones pasadas como datos, operaciones de flujo y tareas concurrentes.

- **Orientado a objetos:** es central en Java. El código se organiza comúnmente en clases, interfaces, objetos, métodos y campos. Hay encapsulación, herencia de clases e implementación de varias interfaces; la herencia de implementación de clases es simple. La orientación a objetos es habitual, pero no obliga a diseñar cada operación como una jerarquía de clases [10].
- **Imperativo, estructurado y procedimental:** Java expresa secuencias de instrucciones, asignaciones, decisiones, bucles y llamadas a métodos. Puede organizarse con métodos que realizan procedimientos y clases auxiliares; un programa con lógica pequeña puede mantenerse claro sin jerarquías extensas.
- **Funcional:** desde Java 8, lambdas, referencias a métodos, interfaces funcionales y Streams permiten transformar y filtrar datos con un estilo funcional. Java no es puramente funcional: conserva estado mutable, efectos secundarios y control imperativo, y las lambdas se apoyan en tipos de interfaz funcional [20].
- **Declarativo:** Java admite expresar transformaciones y consultas de forma más declarativa mediante Streams, anotaciones, APIs de persistencia u otros DSL. No es un lenguaje declarativo puro; los DSL y frameworks que emplee una aplicación pueden ser bibliotecas de terceros.
- **Concurrente:** la concurrencia forma parte del diseño y de las APIs de la plataforma: puede ejecutarse más de una tarea con hilos, ejecutores y otras abstracciones. La posibilidad de concurrencia no implica que el programa se ejecute en paralelo en varios núcleos; esto depende del hardware, runtime, configuración y carga. La sincronización y seguridad de estado compartido son responsabilidades del diseño de la aplicación [10].
- **Reactivo:** es posible diseñar sistemas que procesen eventos y flujos asíncronos con bibliotecas o frameworks. «Reactivo» no es un único paradigma obligatorio ni una característica que convierta por sí sola a Java SE en un framework reactivo. Debe identificarse la biblioteca y versión elegidas; no se atribuirá aquí una dependencia externa como parte del lenguaje.

**Criterio de selección:** elija el estilo que haga explícitos los datos, las responsabilidades y el flujo del programa. No fuerce orientación a objetos para cálculos simples ni encadene operaciones funcionales complejas solo para evitar un bucle legible.

### Ventajas, límites y criterios de elección

#### Fortalezas

Java combina tipado estático, comprobaciones en compilación, bibliotecas estándar extensas y una plataforma madura. El compilador detecta diversas incompatibilidades antes de ejecutar; la verificación de tipos no elimina errores lógicos, errores de concurrencia ni fallos que solo aparecen ante entradas reales. Su ecosistema incluye herramientas de compilación, pruebas, análisis, empaquetado y observabilidad, pero muchos frameworks y herramientas son proyectos independientes con ciclos de soporte propios [10] [16].

El bytecode y la JVM hacen posible que el mismo artefacto se ejecute en implementaciones compatibles sin compilarlo para una CPU concreta, siempre que la JVM y las APIs necesarias estén presentes. La compilación JIT y la optimización en ejecución pueden ofrecer buen rendimiento sostenido para servicios de larga duración; no existe una garantía de que una aplicación Java sea siempre más rápida, más lenta o más portable que una alternativa. La medición depende de la carga y del runtime elegido [10].

La evolución sostenida del lenguaje y de la plataforma protege inversiones en código de larga vida: el proceso de versiones incorpora compatibilidad y actualizaciones. «Compatible» no significa que toda API interna, dependencia, configuración, driver o función preview permanezca sin cambios. El uso de APIs internas no soportadas crea una deuda de actualización, y los programas deben probarse en cada cambio de runtime objetivo [21] [22].

#### Límites y costes que conviene evaluar

Java necesita un runtime compatible, ya sea instalado junto a la aplicación o incorporado en su imagen de despliegue. Según la aplicación y la build, el arranque, el tamaño de la imagen y el consumo de memoria pueden ser mayores que en un binario nativo muy pequeño. Las optimizaciones JIT pueden requerir calentamiento y la recolección de basura automatiza la administración de memoria, pero no elimina pausas, presión de memoria, fugas lógicas ni la necesidad de medir. Estos costes dependen de la aplicación, JVM, recolector, opciones y sistema operativo; no son constantes de todo Java [10].

El lenguaje ofrece menos control directo sobre la representación de bajo nivel que C o C++. No permite manipular punteros ordinarios de forma general y segura desde el código Java; para hardware muy restringido, sistemas operativos, kernels o código que exija control fino de memoria y ABI, puede ser preferible un lenguaje de sistemas, o bien separar una capa nativa cuidadosamente mantenida. Java Native Interface u otras APIs específicas permiten interoperar con código nativo, pero añaden riesgos de portabilidad, seguridad y mantenimiento.

La compatibilidad de aplicaciones complejas suele depender de bibliotecas externas, herramientas de build, base de datos, drivers y entorno de despliegue. El cambio de versión de Java puede ser sencillo en algunos proyectos y exigir trabajo en otros. Antes de elegir una versión, confirma que frameworks y productos de terceros la soporten. Una versión GA muy nueva no equivale a una versión con soporte prolongado para todos los proveedores.

#### Casos de uso adecuados

Java suele ser una elección sólida para servicios web y APIs, aplicaciones empresariales, procesamiento de datos, herramientas de backend, sistemas transaccionales y aplicaciones de larga duración que se benefician de bibliotecas maduras, tipado estático y un runtime administrado. También se utiliza para aplicaciones de escritorio con las APIs disponibles o bibliotecas gráficas adicionales, y para desarrollar software en plataformas móviles como Android, aunque Android ejecuta aplicaciones en Android Runtime y no debe confundirse con una JVM Java SE convencional. En sistemas de IoT y dispositivos embebidos, la conveniencia depende del dispositivo, memoria disponible, runtime y edición/plataforma requerida; Java SE general no equivale a Java Card [10] [13] [24].

#### Cuándo evaluar otra opción

Considere otra tecnología si el objetivo es ejecutar sin runtime en un microcontrolador mínimo, acceder directamente a instrucciones o memoria específicas, minimizar de manera extrema el tamaño de una herramienta de línea de comandos de arranque instantáneo, o cumplir restricciones de tiempo real estrictas que su implementación Java concreta no pueda demostrar. Para un cliente web que se ejecuta en navegador, Java no sustituye directamente a JavaScript o WebAssembly. Para un prototipo de automatización muy pequeño, otro lenguaje puede tener un ciclo de entrega más corto. Estas son decisiones de contexto: Java tiene opciones de compilación nativa, runtimes especializados e implementaciones particulares, pero no deben asumirse como propiedades uniformes del Java SE estándar.

### Primer ejemplo conceptual

El programa siguiente muestra un archivo fuente Java tradicional. Usa únicamente sintaxis básica y no requiere bibliotecas externas.

```java
// HolaJava.java
public class HolaJava {
    public static void main(String[] args) {
        String lenguaje = "Java";
        System.out.println("Hola, " + lenguaje + "!");
    }
}
```

Desde el directorio que contiene `HolaJava.java`, compílelo y ejecútelo con un JDK instalado:

```text
javac HolaJava.java
java HolaJava
```

**Salida esperada:**

```text
Hola, Java!
```

`javac` compila el fuente y crea `HolaJava.class` con bytecode. El lanzador `java` inicia el runtime, carga la clase y llama al método `main`. `String` es un tipo de la plataforma estándar; `System.out.println` escribe una línea en la salida estándar. El nombre del archivo coincide con la clase pública para que la compilación convencional sea directa. La salida indicada es la esperada según el programa; **no afirmo que este ejemplo se haya ejecutado en el entorno de elaboración**. El entorno disponible para esta redacción contenía un runtime OpenJDK 21 pero no `javac`, por lo que no permitió compilarlo aquí [10] [16].

Una forma común de principiante de describir el proceso es «el código se compila a bytecode y después la JVM lo ejecuta». Es una síntesis útil, pero no implica que siempre exista un archivo `.class` visible ni que el bytecode se interprete exclusivamente: desde JDK 11, el lanzador `java` también puede compilar y ejecutar un único archivo fuente en modo fuente. Para un proyecto normal, el flujo de build, pruebas y empaquetado se gestiona con herramientas de proyecto y no debe confundirse con el significado de Java SE [16].

**Errores frecuentes en el primer programa:** omitir el punto y coma al final de una sentencia; escribir `system` en vez de `System` (Java distingue mayúsculas y minúsculas); compilar desde una carpeta distinta a la del archivo; invocar `java HolaJava.java` pensando que es el flujo tradicional de bytecode sin considerar el modo de fuente; instalar solo un runtime cuando se necesita `javac`; o ejecutar otro `java`/`javac` por una configuración de `PATH` incoherente.

**Recomendación:** para aprender, empieza con un JDK compatible con Java 25 LTS, comprueba proveedor y versión con `java -version` y `javac -version`, y conserva el mismo JDK para compilar y ejecutar. Más adelante configura el proyecto para declarar explícitamente su versión mínima de Java, las dependencias y el sistema de build.

## 2. Sintaxis y semántica

La **sintaxis** determina qué secuencias de caracteres y tokens acepta la gramática del lenguaje. La **semántica** determina qué significan esas construcciones: qué nombres designan, qué tipos tienen las expresiones y qué efecto produce ejecutar una instrucción. El JLS separa explícitamente la gramática léxica —caracteres, tokens, comentarios— de la gramática sintáctica —cómo se combinan los tokens en programas— [25] [26].

Un programa puede estar bien formado sintácticamente y, aun así, ser rechazado durante la compilación por un error de tipos o de nombre. También puede compilar y fallar durante la ejecución, o producir un resultado equivocado sin lanzar ninguna excepción. Conviene diagnosticar estos casos por separado, en vez de llamar “error de sintaxis” a todo problema [25] [26] [27].

### 2.1. Estructura básica de un archivo Java

En la forma tradicional, un archivo fuente contiene opcionalmente la declaración `package`, después las declaraciones `import` y, a continuación, declaraciones de tipos como clases, interfaces, enumeraciones o registros. Cada clase agrupa campos, constructores y métodos; un método contiene instrucciones dentro de llaves [28].

```java
package ejemplo;                 // opcional; primero si se usa

import java.util.List;           // opcional; después de package

public class HolaJava {          // clase de nivel superior
    public static void main(String[] args) {  // punto de entrada convencional
        String saludo = "Hola, Java";
        System.out.println(saludo);
    }
}
```

En el flujo tradicional de `javac`, es habitual guardar la clase pública `HolaJava` en `HolaJava.java`. La asociación entre nombres y archivos depende en parte del sistema de archivos y del compilador; no es una regla que convierta los nombres de archivo en tokens de la gramática. Para un programa pequeño sin declaración `package`, la forma de ejecución directa es `java HolaJava.java`; para compilar primero, se usan `javac HolaJava.java` y luego `java HolaJava`. El lanzador de Java también admite modo de archivo fuente, en el que compila el archivo en memoria y lo ejecuta [28] [29].

**Ejecución verificada.** El ejemplo anterior, guardado con el nombre mostrado, se probó con el lanzador de código fuente disponible en este entorno:

```bash
java HolaJava.java
```

Salida observada:

```text
Hola, Java
```

La prueba se hizo con OpenJDK Runtime 21.0.12.1. No se usó `javac`, que no está instalado aquí. Por ello, esta observación verifica el modo de archivo fuente para el ejemplo, no la compilación separada ni la ejecución de características exclusivas de Java 25. El texto esperado para otros ejemplos de esta sección se presenta como consecuencia de su código y no como una ejecución local comprobada.

#### Punto de entrada `main`

Para máxima compatibilidad, especialmente al aprender con proyectos y herramientas que usan muchas versiones, se recomienda empezar por la declaración convencional:

```java
public static void main(String[] args) {
    // instrucciones
}
```

El lanzador clásico busca un método `main` público, estático, sin valor de retorno y con un parámetro `String[]` (también puede escribirse `String...`). El arreglo contiene los argumentos de la línea de comandos. Una clase puede compilar aunque no ofrezca un punto de entrada; la invocación como aplicación falla si el lanzador no encuentra un `main` admisible [29].

**Java 25 y versiones posteriores:** Java 25 finalizó, mediante JEP 512, los *compact source files* y los métodos `main` de instancia. Para programas simples se puede omitir la declaración explícita de clase y escribir, por ejemplo:

```java
void main() {
    IO.println("Hola, Java 25");
}
```

También se puede conservar una clase explícita y usar un `main` de instancia compatible con el protocolo ampliado. Estos formatos no son pseudocódigo ni una característica preliminar en Java 25; JEP 512 está marcado como entregado en esa versión. No deben usarse si el proyecto debe compilar con JDK anteriores a 25. La clase `java.lang.IO` es parte de las facilidades de Java 25 para E/S básica y no se debe confundir con una API de versiones anteriores [30]. La salida esperada del fragmento es `Hola, Java 25`; no se verificó localmente porque el runtime disponible es OpenJDK 21.

### 2.2. Bloques, llaves e indentación

Un **bloque** es una secuencia de declaraciones locales y sentencias delimitada por `{` y `}`. Sirve para agrupar instrucciones, definir el cuerpo de métodos y controlar el alcance de variables locales. Java permite bloques dentro de bloques; las variables locales declaradas dentro de uno no se pueden usar fuera del ámbito que las contiene [26] [27].

```java
public class Bloques {
    public static void main(String[] args) {
        int puntos = 12;

        if (puntos >= 10) {
            String resultado = "aprobado";
            System.out.println(resultado);
        }

        // resultado no está en alcance aquí
    }
}
```

Las llaves tienen función sintáctica: una llave omitida o mal ubicada puede cambiar qué sentencia pertenece a un `if`, un bucle o un método, o provocar que el compilador rechace el archivo. La sangría, en cambio, **no delimita bloques** y no suele cambiar el significado del programa; se usa para hacer visible la estructura que ya expresan las llaves. Como convención profesional, usa cuatro espacios por nivel, alinea llaves de forma consistente y evita mezclar tabuladores y espacios dentro del equipo.

Sin llaves, un `if` o un bucle controla solo una sentencia. Por legibilidad y para prevenir cambios accidentales de alcance, se recomienda escribir llaves incluso cuando el cuerpo tiene una sola instrucción:

```java
if (activo) {
    registrarAcceso();
}
```

El `;` inmediatamente después de una condición también puede representar una **sentencia vacía**; no es una forma de abrir un bloque. Por ejemplo, `if (activo);` compila en contextos válidos, pero su cuerpo no hace nada y la instrucción siguiente queda fuera del `if`. Es un error frecuente y difícil de detectar visualmente [26].

### 2.3. Punto y coma y sentencias

El punto y coma termina muchas declaraciones y sentencias: declaraciones de variables locales, asignaciones, llamadas a métodos, `return`, `break`, `continue`, `throw` y expresiones usadas como sentencias. Java no usa normalmente el salto de línea como terminador, de modo que una expresión puede continuar en otra línea si la gramática lo permite [26] [27].

```java
int cantidad = 3;
int precio = 7;
int total = cantidad * precio;
System.out.println(total);
```

Salida esperada:

```text
21
```

No se añade un punto y coma tras el bloque de un método, una clase o un `if` ordinario. En cambio, el `for` clásico contiene dos puntos y coma dentro de sus paréntesis, separando inicialización, condición y actualización:

```java
for (int i = 0; i < 3; i++) {
    System.out.println(i);
}
```

Salida esperada: `0`, `1` y `2`, cada uno en una línea. Quitar un punto y coma necesario produce un error de compilación; añadirlo después de `if (condición)` puede introducir una sentencia vacía. Evita confiar en la inserción automática de terminadores: Java no convierte cada salto de línea en `;`.

### 2.4. Expresiones y sentencias

Una **expresión** combina literales, nombres, operadores y llamadas para designar un valor o una variable, o para producir efectos. Por ejemplo, `precio * cantidad` calcula un valor; `total > 100` produce una condición booleana; `System.out.println(total)` es una invocación de método `void`, cuyo resultado no es un valor utilizable [27].

Una **sentencia** ordena una acción o controla el flujo: una declaración local, un `if`, un bucle, un `return` o una expresión admitida como sentencia. Algunas expresiones pueden aparecer dentro de una sentencia —por ejemplo, a la derecha de una asignación—, pero una expresión no es siempre una sentencia válida por sí sola. Java acepta como sentencias de expresión, entre otras, asignaciones, incrementos/decrementos, creación de objetos e invocaciones de métodos [26] [27].

```java
int base = 8;                  // declaración con inicialización
int doble = base * 2;           // expresión aritmética en la asignación
boolean suficiente = doble >= 16;  // expresión relacional

if (suficiente) {               // sentencia de selección
    System.out.println("OK");   // sentencia de invocación
}
```

Salida esperada: `OK`. Los operadores tienen precedencia definida, pero añade paréntesis cuando hagan más clara la intención. Por ejemplo, `a + b * c` multiplica antes de sumar; `(a + b) * c` agrupa la suma primero. El significado también depende de los tipos: `5 / 2` usa división entera y produce `2`, mientras que `5.0 / 2` produce `2.5`.

### 2.5. Identificadores y convenciones de nombres

Un **identificador** es el nombre de una variable, método, clase, paquete u otra entidad declarada. En Java SE 25 puede empezar con un carácter que `Character.isJavaIdentifierStart` considere válido y continuar con caracteres aceptados por `Character.isJavaIdentifierPart`; por eso la gramática permite nombres Unicode, además de letras latinas ASCII. Un dígito no puede ser el primer carácter. La disponibilidad exacta de caracteres Unicode evoluciona junto con la versión de la plataforma [25].

```java
int total2026 = 4;      // válido
int _resultado = 5;     // válido como identificador de varios caracteres
int 2total = 4;         // incorrecto: empieza con dígito
int class = 4;          // incorrecto: palabra reservada
```

`$` y `_` pueden aparecer en las reglas léxicas de identificadores con restricciones; evita `$` en código escrito manualmente, pues suele reservarse para nombres generados. El guion bajo aislado `_` no es un identificador ordinario: es una palabra reservada desde Java 9. En Java moderno se permite en ciertos contextos de variables o patrones sin nombre, pero no para declarar una variable común que luego se consulte; esa facilidad depende de versión y contexto [25].

Las palabras reservadas no pueden utilizarse como nombres. En Java SE 25 incluyen, por ejemplo, `class`, `public`, `static`, `void`, `if`, `else`, `for`, `while`, `return`, `new`, `int`, `boolean`, `try`, `catch`, `throw`, `extends`, `implements`, `switch`, `this` y `_`; también siguen reservadas `const` y `goto`, aunque no se emplean en código Java normal. `true`, `false` y `null` son literales, no palabras clave. Términos como `record`, `var`, `yield`, `sealed` y `module` son **palabras clave contextuales**: su tratamiento depende del lugar en que aparezcan, por lo que no equivalen en todos los usos a una palabra reservada clásica [25]. La especificación contiene la lista normativa completa.

Para tener una referencia concreta, las **palabras reservadas** de Java SE 25 son:

```text
abstract, continue, for, new, switch,
assert, default, if, package, synchronized,
boolean, do, goto, private, this,
break, double, implements, protected, throw,
byte, else, import, public, throws,
case, enum, instanceof, return, transient,
catch, extends, int, short, try,
char, final, interface, static, void,
class, finally, long, strictfp, volatile,
const, float, native, super, while,
_ (guion bajo aislado)
```

La JLS define además estas **palabras clave contextuales**: `exports`, `module`, `non-sealed`, `open`, `opens`, `permits`, `provides`, `record`, `requires`, `sealed`, `to`, `transitive`, `uses`, `when`, `with`, `yield` y `var`. `non-sealed` cuenta como una secuencia contextual; `var` también es contextual y su tratamiento depende de la producción gramatical. `strictfp` permanece reservado, pero es obsoleto y no debe usarse en código nuevo [25].

Java distingue mayúsculas y minúsculas: `cuenta`, `Cuenta` y `CUENTA` son nombres diferentes. Sigue convenciones reconocibles, aunque no obligatorias: `PascalCase` para clases (`Factura`), `camelCase` para métodos y variables (`calcularTotal`) y `MAYUSCULAS_CON_GUION_BAJO` para constantes declaradas `static final` (`MAX_INTENTOS`). No uses nombres que solo difieran en mayúsculas: son fáciles de confundir y pueden causar problemas en sistemas de archivos que no distinguen el caso.

### 2.6. Comentarios y documentación

Los comentarios ordinarios son ignorados por el compilador como instrucciones. Java reconoce comentarios de fin de línea (`// ...`), comentarios de bloque (`/* ... */`) y comentarios de documentación (`/** ... */`) que herramientas como Javadoc pueden procesar. Los comentarios de bloque **no se anidan**: un `/*` dentro de otro comentario no abre un segundo nivel [25].

```java
// Comentario de una línea
int intentos = 3; /* comentario corto de bloque */

/**
 * Devuelve el doble de un entero.
 * @param valor número de entrada
 * @return valor multiplicado por dos
 */
static int duplicar(int valor) {
    return valor * 2;
}
```

Un comentario útil explica el motivo, una restricción o una decisión que el código por sí solo no deja clara. Evita comentarios que repitan literalmente la instrucción. Recuerda que texto entre comillas no es un comentario, aunque contenga `//` o `/*`; el compilador lo interpreta como parte de una cadena o un bloque de texto [25].

### 2.7. Indentación, formato y continuidad de línea

Como las llaves y los separadores determinan la estructura, Java permite variar espacios y saltos de línea sin cambiar la mayoría de las construcciones. Por legibilidad, unifica el formato del equipo y utiliza un formateador integrado en el IDE o configurado en el proyecto. La continuación de expresiones puede aprovechar paréntesis y saltos de línea; no dividas identificadores o literales arbitrariamente ni dependas de que el formato visual altere la gramática.

```java
int subtotal = precioUnitario
        * cantidad;

boolean elegible = (edad >= 18)
        && tienePermiso;
```

Ambas expresiones se interpretan como una unidad según sus delimitadores. En proyectos colaborativos, ejecuta el formateador antes de revisar cambios y evita que distintas reglas de llaves o tabulación produzcan diffs ruidosos.

### 2.8. Clases, métodos y archivos: errores de forma comunes

En una clase, los campos y métodos se declaran dentro de sus llaves. Las instrucciones ejecutables ordinarias pertenecen a un método, constructor o bloque de inicialización; no se escriben sueltas en el cuerpo de una clase tradicional. Los nombres de las llaves deben estar balanceados y las declaraciones de métodos requieren tipo de retorno, nombre, paréntesis y cuerpo o terminador válido según su contexto.

Incorrecto en una clase tradicional:

```java
public class Ejemplo {
    System.out.println("No es una declaración de miembro");
}
```

Correcto:

```java
public class Ejemplo {
    public static void main(String[] args) {
        System.out.println("Esta llamada está dentro de un método");
    }
}
```

La excepción moderna es el formato compacto de Java 25 descrito arriba, donde el cuerpo fuente puede declarar miembros sin escribir explícitamente la clase. No mezcles sintaxis de ese formato con una base anterior ni asumas que todo fragmento de documentación es directamente ejecutable como archivo Java: puede ser un fragmento que presupone una clase o método contenedor [28] [30].

### 2.9. Tipos de errores: de la gramática a la lógica

**Error sintáctico.** La secuencia de tokens no coincide con la gramática. Ejemplos: omitir `;` donde es necesario, escribir `if edad > 18` sin paréntesis o dejar una llave sin pareja. El compilador suele señalar la línea o un token cercano; el punto indicado puede ser posterior al lugar real del fallo.

```java
int edad = 20  // incorrecto: falta ;
```

```java
int edad = 20; // correcto
```

**Error de compilación no necesariamente sintáctico.** El programa puede tener una estructura gramatical válida pero infringir reglas estáticas, por ejemplo asignar una cadena a un `int`, usar un nombre no declarado, acceder a un miembro inaccesible o leer una variable local sin inicializar. La expresión “error semántico” se usa de distintas maneras en cursos y compiladores; para Java resulta más preciso decir **error de compilación** y aclarar si se trata de gramática, tipos, nombres, accesibilidad o reglas estáticas [25] [26].

```java
int cantidad = "tres"; // sintaxis reconocible, pero tipos incompatibles
```

**Excepción o error en ejecución.** El código compila, pero durante la ejecución ocurre una condición excepcional, como dividir un entero por cero, acceder a través de una referencia `null` o usar un índice fuera de rango. La división entera por cero, por ejemplo, produce `ArithmeticException`; no debe confundirse con el error de compilación que generaría una operación de tipos incompatibles [27].

**Error lógico.** El programa compila y puede terminar normalmente, pero resuelve mal el problema: una comparación invertida, una fórmula equivocada o no tratar un caso límite. No existe necesariamente un mensaje de error del compilador o de la JVM. Pruebas con entradas normales, límites y casos inválidos ayudan a descubrirlo.

#### Diagnóstico progresivo

1. **Lee primero el primer diagnóstico del compilador.** Los posteriores pueden ser consecuencia del primero, especialmente tras una llave o un punto y coma omitido.
2. **Verifica delimitadores y tokens:** `{}`, `()`, `[]`, `;`, comillas y palabras reservadas.
3. **Revisa nombres y tipos:** declaración visible, ortografía exacta, mayúsculas, tipo esperado y conversiones.
4. **Si compila, examina la excepción:** tipo, mensaje y primera línea de la traza que pertenece a tu código.
5. **Si no hay excepción, compara resultado y requisito:** crea pruebas que separen casos típicos, bordes y entradas no válidas.

Los mensajes y códigos de diagnóstico pueden variar entre `javac`, el IDE, la versión del JDK, el sistema operativo y el proveedor. El comportamiento exigido por el lenguaje lo define la especificación, pero el texto y la ubicación exacta de un mensaje no son portables.

### 2.10. Ejemplo integrado: sintaxis, ejecución y salida

El siguiente archivo combina identificadores, mayúsculas/minúsculas, expresiones, sentencias, bloque y punto de entrada convencional:

```java
public class Saludo {
    public static void main(String[] args) {
        String nombre = args.length == 0 ? "Java" : args[0];
        System.out.println("Hola, " + nombre + "!");
    }
}
```

Modo de archivo fuente con JDK 11 o posterior:

```bash
java Saludo.java
java Saludo.java Ada
```

Salida esperada, de acuerdo con el código:

```text
Hola, Java!
Hola, Ada!
```

La primera línea de ejecución usa el valor alternativo cuando no se pasan argumentos; la segunda toma `Ada` de `args[0]`. Este ejemplo se ejecutó realmente en el entorno disponible con un nombre de archivo equivalente (`HolaJava.java`) y produjo `Hola, Java!` y `Hola, Ada!`. La ejecución observada se hizo con OpenJDK 21.0.12.1 y no prueba por sí sola la compilación tradicional con `javac` ni las novedades de Java 25.

### 2.11. Errores frecuentes y recomendaciones

- **Omitir `;`** al final de una declaración o asignación. Comprueba primero la sentencia anterior al lugar donde el compilador marca el problema.
- **Poner `;` tras el `if`** y dejar sin efecto el bloque siguiente. Evita sentencias vacías involuntarias y usa llaves.
- **Desbalancear llaves** o pegar un método fuera de la clase. Indenta con el IDE y revisa el contorno de cada bloque.
- **Usar `=` en vez de `==`** al comparar. En Java la asignación y la igualdad son operaciones distintas; una expresión booleana debe usar un operador de comparación adecuado.
- **Confundir mayúsculas** en nombres de clases, métodos y variables. Conserva la grafía exacta de las declaraciones.
- **Intentar usar palabra reservada como nombre** (`int class = 1`). Escoge un identificador descriptivo distinto.
- **Escribir declaraciones dentro del lugar equivocado.** Las declaraciones de campos pertenecen al cuerpo de clase; las variables locales, a un método o bloque.
- **Usar un `main` no reconocido por el JDK objetivo.** Para compatibilidad amplia, conserva `public static void main(String[] args)`; reserva compact source files y entry points de instancia para Java 25+ y configura el `--release` o la versión del proyecto consecuentemente [29] [30].
- **Creer que compilar demuestra que el programa es correcto.** El compilador valida reglas del lenguaje; no certifica que el algoritmo cumpla el requisito. Añade pruebas y revisiones.

Como hábito profesional, compila y prueba con el JDK objetivo, configura el IDE para esa versión, mantén el formato consistente y no copies un snippet sin identificar el contenedor o la versión que presupone. Para investigar una construcción dudosa, consulta primero el capítulo correspondiente del JLS de la versión objetivo y después la documentación del compilador o del IDE usado.

## 3. Tipos de datos y sistema de tipos

### 3.1 Modelo del sistema de tipos

Java es un lenguaje **estáticamente tipado**: toda variable y expresión tiene un tipo conocido en tiempo de compilación. El compilador comprueba compatibilidad, operaciones permitidas y buena parte de los errores de tipos antes de ejecutar el programa. La ejecución sigue siendo dinámica en otros sentidos: la JVM carga clases y la selección de métodos sobrescritos ocurre según el objeto concreto, pero esto no convierte el lenguaje en dinámicamente tipado [31].

La JLS también describe Java como **fuertemente tipado**: los tipos restringen los valores que una variable puede contener, las operaciones disponibles y el significado de esas operaciones. “Fuerte” y “débil” no tienen una escala universal independiente de las reglas de cada lenguaje; es más preciso explicar qué conversiones Java permite automáticamente y cuáles exige expresar o comprobar [31] [32].

Java separa **tipos primitivos** de **tipos de referencia**. Una variable primitiva contiene un valor primitivo de su tipo. Una variable de referencia puede contener `null` o una referencia compatible con el tipo declarado. Si la referencia no es nula, apunta a un objeto cuya clase concreta debe ser compatible con el tipo estático de la expresión [31]. El modelo del lenguaje no ofrece aritmética de punteros ni permite inspeccionar o manipular directamente una dirección de memoria.

```java
Number dato = Integer.valueOf(42); // Tipo estático: Number; objeto concreto: Integer
System.out.println(dato.intValue());
```

El compilador solo permite en `dato` las operaciones disponibles para `Number`, salvo que se compruebe o convierta el tipo. La llamada a `intValue()` es válida porque pertenece a `Number`. En cambio, una operación propia de `Integer` no queda disponible solo porque el objeto real sea un `Integer`. Esta distinción entre **tipo estático** (conocido al compilar) y clase concreta del objeto es central para entender interfaces, herencia, conversiones y patrones.

### 3.2 Tipos primitivos

Los ocho tipos primitivos son palabras reservadas. Siete son numéricos y `boolean` representa valores lógicos. Sus tamaños y rangos numéricos están definidos por la especificación, no dependen del procesador ni del sistema operativo [31].

| Tipo | Categoría y representación especificada | Valores / matices |
|---|---|---|
| `byte` | Entero con signo de 8 bits, complemento a dos | −128 a 127 |
| `short` | Entero con signo de 16 bits, complemento a dos | −32 768 a 32 767 |
| `int` | Entero con signo de 32 bits, complemento a dos | −2³¹ a 2³¹−1; tipo usual para enteros |
| `long` | Entero con signo de 64 bits, complemento a dos | −2⁶³ a 2⁶³−1; los literales suelen llevar sufijo `L` |
| `char` | Unidad de código UTF-16 sin signo de 16 bits | `0` a `65 535`; no equivale necesariamente a un carácter Unicode completo |
| `float` | IEEE 754 binary32 | Aproximado; literal con sufijo `f` o `F` |
| `double` | IEEE 754 binary64 | Aproximado; tipo predeterminado para literales decimales |
| `boolean` | Tipo lógico | Solo `true` y `false`; no se convierte a número |

`char` contiene una **unidad de código UTF-16**, no necesariamente un punto de código Unicode completo. Algunos caracteres Unicode requieren un par sustituto (dos valores `char`); para recorrer texto como puntos de código, se usan las API de `String` como `codePoints()`. Tampoco debe confundirse `char` con un pequeño entero con signo: su rango es de 0 a 65 535 [31].

Los enteros no detectan desbordamiento aritmético lanzando una excepción: el resultado de las operaciones enteras se ajusta al tamaño del tipo. `float` y `double` siguen IEEE 754 e incluyen valores como infinito y NaN; por tanto, comparar decimales binarios con `==` puede ser inadecuado para cálculos que requieren exactitud decimal. Para dinero u otros importes decimales exactos suele ser preferible `BigDecimal`, construido desde texto, por ejemplo `new BigDecimal("0.10")` [32] [33].

```java
int maximo = Integer.MAX_VALUE;
System.out.println(maximo + 1);
System.out.println(0.1 + 0.2);
```

Salida esperada:

```text
-2147483648
0.30000000000000004
```

La primera operación desborda de manera circular en `int`. La segunda refleja que los valores binarios de punto flotante no representan exactamente muchos decimales; no es un error exclusivo de Java. Para `BigDecimal`, usa cadenas decimales y define escala y redondeo explícitamente cuando corresponda. `new BigDecimal(0.1)` captura el valor binario aproximado de `double` y suele sorprender; la API documenta la diferencia respecto de `new BigDecimal("0.1")` [33].

### 3.3 Tipos de referencia: clases, interfaces y arrays

Son tipos de referencia las **clases**, **interfaces** y **arrays**. Además, los tipos parametrizados de genéricos, como `List<String>`, son tipos de clase o interfaz. Una interfaz no se instancia directamente: una variable declarada con tipo de interfaz puede referirse a una instancia de una clase que la implemente. El tipo declarado determina qué miembros puede invocar el código; la clase real del objeto puede ser una implementación diferente [31].

```java
CharSequence texto = new StringBuilder("Java");
System.out.println(texto.length());
```

`texto` tiene tipo estático `CharSequence`, por lo que `length()` está disponible. Aunque el objeto concreto sea `StringBuilder`, no puede invocarse directamente un método exclusivo de `StringBuilder` mediante la referencia `texto` sin una conversión apropiada. En código profesional conviene declarar variables y parámetros usando interfaces cuando el consumidor no necesite detalles de una implementación específica.

#### Arrays

Un array es un objeto de longitud fija cuyos elementos tienen un tipo. La longitud se consulta con `.length`, los índices empiezan en cero y cada acceso está sujeto a comprobación de límites en tiempo de ejecución. Declarar una variable `int[] valores;` no crea el array; `new int[3]` sí lo crea. Los elementos reciben valores por defecto: cero para tipos numéricos, `false` para `boolean` y `null` para referencias. Estos valores por defecto aplican a campos y componentes de arrays; las variables locales deben inicializarse antes de leerse [31] [34].

```java
int[] numeros = new int[3];
String[] nombres = {"Ada", "Lin"};
numeros[0] = 7;
System.out.println(numeros.length + ", " + numeros[1] + ", " + nombres[0]);
```

Salida esperada:

```text
3, 0, Ada
```

Los arrays de referencias son covariantes: `String[]` puede asignarse a `Object[]`. Esa flexibilidad puede producir `ArrayStoreException` al guardar en tiempo de ejecución un elemento cuyo tipo no corresponda al array real. En contraste, los genéricos ordinarios son invariantes: `List<String>` no es un subtipo de `List<Object>` [31] [34]. Para colecciones de tamaño variable y control de tipos más seguro suele convenir `List<T>`; el array sigue siendo apropiado para tamaños fijos, interoperabilidad y ciertas APIs.

#### Arrays multidimensionales

`int[][]` es un array de referencias a otros arrays, no necesariamente una matriz rectangular. Cada fila puede tener una longitud distinta o incluso ser `null`. Si se crea con `new int[2][31]`, se crean inicialmente dos filas de tres enteros, pero es posible sustituirlas después por filas de distinta longitud. La longitud de un array existente no cambia; para cambiarla, se crea otro array [34].

### 3.4 `null` y ausencia de valor

`null` es la única expresión del tipo especial **tipo nulo**. No es un valor de tipo primitivo ni una instancia de `Object`; puede asignarse a cualquier variable de referencia, pero no a una primitiva. Una variable de referencia sin inicializar, si es un campo, recibe `null` por defecto; una variable local no tiene valor por defecto y el compilador impide leerla antes de asignarla [31].

```java
String nombre = null;
// int cantidad = null; // Error de compilación

if (nombre == null) {
    System.out.println("No se proporcionó nombre");
}
```

No se debe usar `==` para comparar contenido textual: `==` compara si dos referencias son la misma referencia; `String.equals` compara contenido. Para probar el nulo, `referencia == null` es correcto. Invocar un método o acceder a un miembro a través de `null` lanza `NullPointerException` [32].

Para representar explícitamente que un método puede no producir resultado, Java ofrece `Optional<T>`. La API recomienda su uso principalmente como tipo de retorno cuando existe una ausencia legítima; la variable `Optional` en sí no debería ser `null`. `Optional` no sustituye la validación ni garantiza por sí solo que los objetos internos sean inmutables [35]. En modelos donde la ausencia tenga significado propio, también pueden ser apropiados un tipo de resultado específico o una jerarquía sellada.

### 3.5 Boxing y unboxing

Las clases envoltorio (wrapper) emparejan primitivas con tipos de referencia: `Boolean`, `Byte`, `Short`, `Integer`, `Long`, `Character`, `Float` y `Double`. **Boxing** convierte automáticamente una primitiva a su wrapper; **unboxing** extrae la primitiva de un wrapper. También puede hacerse explícitamente mediante `Integer.valueOf(...)` y `intValue()`, por ejemplo [32] [36].

```java
Integer envuelto = 12; // boxing
int primitivo = envuelto; // unboxing
System.out.println(primitivo + 1);
```

Salida esperada: `13`.

Un wrapper puede ser `null`; al intentar desenvolverlo, se lanza `NullPointerException`. La conversión automática puede aparecer en expresiones, argumentos y colecciones genéricas, aunque los tipos genéricos no admiten primitivas directamente (`List<int>` no es válido; se usa `List<Integer>`). Las conversiones automáticas son cómodas, pero conviene evitar unboxing de datos potencialmente nulos y no depender de `==` para comparar wrappers: para comparar valores, úsese `equals` o una conversión controlada a primitiva [32] [36].

```java
Integer posibleNulo = null;
// int valor = posibleNulo; // Compila, pero falla en ejecución con NullPointerException
```

`Integer.valueOf` garantiza caché para valores entre −128 y 127, inclusive; puede cachear más, pero no debe asumirse. Esto no convierte la identidad del wrapper en una forma válida de comparar números. Los wrappers de primitivas son clases **value-based**: la API recomienda tratarlos según su valor y no usarlos como monitores de sincronización [36].

### 3.6 Conversiones, casting y narrowing

Una conversión hace que un valor de un tipo se interprete o transforme para otro contexto. Algunas son implícitas; otras requieren una conversión explícita (cast). Las categorías de la JLS incluyen conversiones primitivas, de referencia, boxing/unboxing y conversiones no comprobadas de genéricos [32].

#### Conversión primitiva de ampliación (*widening*)

Una conversión de ampliación permite asignar directamente tipos que tienen un dominio de destino más amplio, por ejemplo `int` a `long`, o `float` a `double`. Sin embargo, “widening” no significa que siempre conserve toda precisión: convertir `int` o `long` a `float`, o `long` a `double`, puede redondear los bits menos significativos, aunque no se lanza una excepción [32].

```java
int habitantes = 1_234_567;
long total = habitantes;       // ampliación
float aproximado = habitantes; // ampliación, pero puede perder precisión
```

#### Conversión primitiva de estrechamiento (*narrowing*)

Una conversión de estrechamiento puede descartar rango o precisión y normalmente exige un cast explícito. Un cast no comprueba que el valor quepa en el destino. Al convertir un entero a un entero menor se conservan los bits bajos, de modo que el resultado puede cambiar de magnitud o signo. Al convertir de punto flotante a entero, Java trunca hacia cero la parte fraccionaria; los casos fuera de rango y NaN se rigen por reglas específicas de la JLS, no por una excepción de desbordamiento [32].

```java
int original = 130;
byte reducido = (byte) original;
int truncado = (int) 9.8;
System.out.println(reducido + ", " + truncado);
```

Salida esperada: `-126, 9`.

El ejemplo de `byte` muestra el descarte de bits al estrechar; no debe usarse como comprobación de rango. Para validar datos antes de convertir, comprueba primero el límite (por ejemplo, entre `Byte.MIN_VALUE` y `Byte.MAX_VALUE`) o usa métodos de conversión que detecten desbordamiento, como `Math.toIntExact(long)` cuando aplique. Los literales constantes tienen reglas especiales: `byte b = 10;` compila si el valor constante cabe, mientras que `int variable = 10; byte b = variable;` requiere conversión explícita [32].

#### Conversión de referencia y comprobación en tiempo de ejecución

Una conversión de referencia hacia un supertipo (por ejemplo, `String` a `Object`) es segura sin cast. Una conversión hacia un subtipo puede requerir cast y comprobación en tiempo de ejecución; si el objeto no es compatible se lanza `ClassCastException`. Antes de Java 16 era habitual usar `instanceof` seguido de cast; actualmente el patrón de tipo evita duplicar la comprobación [32] [37].

```java
Object valor = "tipado";
if (valor instanceof String cadena) {
    System.out.println(cadena.toUpperCase());
}
```

Salida esperada: `TIPADO`. El patrón solo queda disponible en el ámbito donde el flujo de control garantiza que coincidió. Esta forma es estable desde Java 16; no confundirla con los patrones de tipo primitivo de JDK 27, que siguen siendo preview [37] [38].

### 3.7 Promoción numérica

Antes de aplicar operadores aritméticos, Java promueve operandos a un tipo común conforme a reglas definidas. En muchas operaciones aritméticas, `byte`, `short` y `char` se promocionan a `int`; por eso, aunque ambos operandos sean `byte`, el resultado de `a + b` es `int`. Si participa `double`, el tipo promovido es `double`; si no, pero participa `float`, es `float`; si no, pero participa `long`, es `long`; de otro modo suele ser `int` [32].

```java
byte a = 10;
byte b = 20;
int suma = a + b; // a y b se promueven a int
// byte sumaPequena = a + b; // Error: el resultado es int
byte sumaReducida = (byte) (a + b);
System.out.println(suma + ", " + sumaReducida);
```

Salida esperada: `30, 30`.

Las asignaciones compuestas (`+=`, `-=`, etc.) incluyen una conversión implícita de vuelta al tipo de la variable, a diferencia de la asignación simple. Así, `b += 1` puede compilar donde `b = b + 1` no lo hace, pero el resultado aún puede truncarse. No se debe usar esta diferencia para ocultar una posible pérdida de rango. Al combinar wrappers con operadores numéricos se produce unboxing; si uno es `null`, la expresión puede fallar con `NullPointerException` [32].

### 3.8 Mutabilidad e inmutabilidad

La **mutabilidad** describe si el estado observable de un objeto puede cambiar después de crearse. No es lo mismo que poder reasignar una variable. Una referencia declarada `final` no puede apuntar a otro objeto una vez asignada, pero el objeto referenciado podría seguir siendo mutable. A la inversa, una variable no final puede apuntar sucesivamente a distintas instancias inmutables.

```java
final List<String> nombres = new ArrayList<>();
nombres.add("Ada");                 // Válido: se muta el objeto
// nombres = new ArrayList<>();     // Error: la referencia es final
```

`String`, los wrappers y `BigDecimal` son ejemplos de clases inmutables o value-based cuya API debe usarse según sus contratos. Un array, en cambio, es mutable aunque la referencia a él sea `final`. `List.of(...)` devuelve una lista no modificable mediante esa referencia, pero “no modificable” no significa necesariamente inmutabilidad profunda: sus elementos referenciados podrían cambiar, y otras estructuras pueden exponer vistas no modificables sobre datos aún mutables [33] [35] [36].

Los records (siguiente sección) hacen finales sus componentes, pero esa inmutabilidad es superficial si un componente referencia un array, una lista mutable u otro objeto mutable. Para construir tipos realmente inmutables, usa campos privados finales, no expongas mutadores, valida invariantes, y realiza copias defensivas de colecciones u objetos mutables en entrada y salida cuando el contrato lo requiera.

### 3.9 Genéricos: seguridad estática y *type erasure*

Los genéricos permiten parametrizar clases, interfaces y métodos con tipos, para reutilizar código conservando comprobaciones estáticas. En `List<String>`, por ejemplo, el compilador impide insertar accidentalmente un `Integer` a través de esa vista y permite recuperar elementos como `String` sin cast explícito. Los argumentos de tipo son tipos de referencia: no se puede escribir `List<int>`; se usa `List<Integer>` [31] [39].

```java
static <T> T primero(List<T> elementos) {
    if (elementos.isEmpty()) {
        throw new IllegalArgumentException("La lista debe tener elementos");
    }
    return elementos.get(0);
}

List<String> idiomas = List.of("Java", "Kotlin");
String inicial = primero(idiomas);
```

`T` vincula el tipo de entrada con el tipo de retorno. Los límites acotan operaciones permitidas, por ejemplo `<T extends Number>`. Los genéricos son **invariantes**: aunque `Integer` extiende `Number`, `List<Integer>` no es subtipo de `List<Number>`. Para APIs que consumen o producen tipos relacionados se usan comodines: `? extends T` suele servir para leer productores de `T`; `? super T`, para escribir consumidores de `T` (regla mnemotécnica PECS, no sustituto de entender el contrato) [31] [39].

#### Qué borra exactamente la erasure

Java implementa genéricos principalmente mediante **type erasure** (*borrado de tipos*): se conserva la comprobación genérica en compilación y se traduce el tipo genérico a una representación de ejecución compartida. En términos de la JLS, la erasure de un tipo parametrizado elimina los argumentos de tipo y produce el tipo genérico correspondiente sin parámetros; la erasure de una variable de tipo es la de su primer límite (o `Object` si no se declaró límite); la erasure de un array es el array de la erasure de su tipo de elemento. La firma de un método genérico se transforma sin sus parámetros de tipo, con los tipos de parámetro borrados [31].

De esto se desprenden matices importantes:

- `List<String>` y `List<Integer>` comparten la misma clase genérica en tiempo de ejecución; no se conserva el argumento de tipo como una instancia distinta de clase. Sin embargo, los archivos `.class` pueden incluir metadatos genéricos accesibles a herramientas y reflexión: decir que “se borra todo rastro” es excesivo [31].
- No se puede escribir `obj instanceof List<String>` ni crear normalmente `new T[]`, porque la JVM no puede comprobar en ejecución esos tipos parametrizados concretos; sí se permiten tipos reificables, como `List<?>` en un patrón de comprobación compatible [31].
- Sobrecargar solo por argumentos que se borran igual, como `metodo(List<String>)` y `metodo(List<Integer>)`, es un conflicto de firma tras la erasure.
- El compilador puede insertar casts al recuperar valores y generar métodos puente (*bridge methods*) para preservar polimorfismo al erasure; esto es una parte de la traducción del compilador, no una nueva jerarquía de tipos en ejecución [31].
- Los tipos raw (`List` sin parámetros) existen por compatibilidad heredada. Su uso debilita la comprobación estática y puede provocar *heap pollution* y `ClassCastException`; warnings `unchecked` deben atenderse, no silenciarse sin justificación [31].

Java no tiene tipos genéricos primitivos en Java SE 27: para contenedores numéricos genéricos se emplean wrappers, con posibles operaciones de boxing/unboxing. En código de alto volumen, considera APIs especializadas como `IntStream` o estructuras primitivas de bibliotecas mantenidas si el perfilado demuestra que importa; las bibliotecas externas no cambian las reglas del lenguaje.

### 3.10 Inferencia de tipo local con `var`

Desde Java 10, `var` permite inferir el tipo estático de una variable local a partir de su inicializador. No convierte Java en dinámicamente tipado: una vez inferido, el tipo de la variable no cambia. `var` es un nombre de tipo reservado para este contexto, no una palabra clave general [40].

```java
var nombres = new ArrayList<String>(); // tipo inferido: ArrayList<String>
var cantidad = 3;                       // tipo inferido: int
```

`var` solo se admite en declaraciones locales con inicializador y en variables de iteración `for` permitidas por la especificación. No puede declararse un campo, parámetro o retorno como `var`; no se usa sin inicializador, con `null` como único inicializador, con varias variables declaradas en la misma declaración ni para inferir un tipo de una lambda sin un tipo objetivo. El inicializador influye directamente en el tipo inferido: `var valores = new ArrayList<String>()` tiene tipo `ArrayList<String>`, no el tipo de interfaz `List<String>` que quizá convendría exponer en una API [40].

```java
// Válido: el tipo se infiere de la expresión
var mensaje = "Hola"; // String

// No válidos como declaraciones locales con var:
// var sinValor;
// var desconocido = null;
// var primero = 1, segundo = 2;
// var operacion = x -> x + 1;
```

Usa `var` cuando el tipo sea evidente por el lado derecho y reduzca ruido; conserva un tipo explícito cuando aclare la abstracción, cuando el inicializador no revele intención o cuando evite exponer un tipo de implementación. Es una herramienta de legibilidad, no una meta de reducir cada declaración.

### 3.11 Records: portadores de datos con inmutabilidad superficial

Un **record** es una clase nominal diseñada para modelar un agregado transparente de datos. Su cabecera enumera componentes y el compilador aporta, cuando no se declaran explícitamente, campos finales, accesores con el nombre de cada componente, constructor canónico, `equals`, `hashCode` y `toString`. Los records son permanentes desde Java 16 [41].

```java
record Punto(int x, int y) {
    Punto {
        if (x < 0 || y < 0) {
            throw new IllegalArgumentException("Las coordenadas deben ser no negativas");
        }
    }
}

Punto origen = new Punto(0, 0);
System.out.println(origen.x() + ", " + origen);
```

Salida esperada: `0, Punto[x=0, y=0]`.

El constructor compacto permite validar o normalizar parámetros antes de asignarlos a los componentes. Un record es implícitamente `final`, extiende `java.lang.Record` y no puede extender una clase arbitraria; sí puede implementar interfaces y declarar métodos o miembros estáticos permitidos. Sus componentes son finales, pero no se garantiza inmutabilidad profunda: `record Datos(List<String> valores)` no vuelve inmutable una lista mutable entregada al constructor [41].

Utiliza records para DTO, resultados, claves compuestas y otros datos cuyo estado y API coinciden. No son un reemplazo universal de clases: si se necesita ocultar o cambiar la representación interna, mantener estado mutable, controlar extensibilidad o definir una identidad ajena a todos los componentes, una clase normal puede expresar mejor el diseño. Una implementación personalizada de accesores o `equals` debe respetar el contrato conceptual del estado del record [41].

### 3.12 Clases e interfaces `sealed`

Desde Java 17, una clase o interfaz puede declararse `sealed` para restringir qué tipos pueden extenderla o implementarla. `permits` enumera los subtipos autorizados; si estos se declaran en el mismo archivo fuente, en ciertos casos el compilador puede inferirlos. Los subtipos permitidos deben cumplir las reglas de módulo/paquete y declarar cómo continúa la jerarquía: `final` para cerrarla, `sealed` para seguir restringiéndola o `non-sealed` para reabrirla [42].

```java
sealed interface Resultado permits Exito, Fallo { }
record Exito(String valor) implements Resultado { }
record Fallo(String motivo) implements Resultado { }
```

Aquí el conjunto directo de implementaciones conocidas de `Resultado` queda controlado. Los records implementadores son finales implícitamente. Las jerarquías selladas permiten representar variantes de dominio explícitas y pueden ayudar al compilador a comprobar la exhaustividad de un `switch` con patrones, pero no convierten por sí solas una jerarquía en una unión algebraica ni eliminan la necesidad de considerar evolución binaria, accesibilidad o versiones [42] [43].

### 3.13 Patrones y versiones: lo estable y lo experimental

Un **patrón** expresa una comprobación de forma y, si coincide, introduce variables tipadas. Los patrones de tipo con `instanceof` son permanentes desde Java 16. El *pattern matching for switch* y los record patterns son permanentes desde Java 21; permiten discriminar alternativas y descomponer records, respectivamente [37] [43] [44].

```java
static String describir(Object valor) {
    return switch (valor) {
        case String texto -> "texto de longitud " + texto.length();
        case Integer numero -> "entero " + numero;
        case null -> "ausente";
        default -> "otro tipo";
    };
}
```

El `switch` de patrones puede gestionar `null` mediante `case null`; no debe suponerse que cualquier `switch` acepta automáticamente un selector nulo. La exhaustividad de un `switch` expresión se comprueba en compilación; las clases selladas y records permiten expresar casos conocidos y comprobables. Si se omite `case null`, un selector nulo no coincide mágicamente con otro patrón y el comportamiento debe tratarse conforme a las reglas del switch aplicable [43].

**Matiz de Java 27:** los patrones de tipos primitivos y el uso ampliado de primitivas en patrones, `instanceof` y `switch` continúan siendo una característica **preview** en JDK 27 mediante JEP 532 (quinta preview). No es sintaxis estable ni se habilita por defecto. Para experimentar, la documentación de JEP indica compilar con `javac --release 27 --enable-preview Archivo.java` y ejecutar con `java --enable-preview Archivo`; también requiere un JDK que soporte esa versión preview [38]. No se recomienda para código que deba compilar con JDK 25 LTS u otros JDK sin soporte equivalente. No es una API de terceros ni un incubator: es una característica preview del lenguaje OpenJDK/JDK.

### 3.14 Ejemplo integrador

El siguiente programa reúne referencias, primitivos, arrays, `var`, boxing, genéricos, `null`, records, sealed y patrones estables. Requiere Java 21 o posterior y no usa características preview.

```java
import java.util.List;

sealed interface Estado permits Activo, Suspendido { }
record Activo(String nombre, int puntos) implements Estado { }
record Suspendido(String motivo) implements Estado { }

public class TiposDemo {
    static String resumen(Estado estado) {
        return switch (estado) {
            case Activo(var nombre, var puntos) -> nombre + ": " + puntos;
            case Suspendido(var motivo) -> "Suspendido: " + motivo;
            case null -> "Sin estado";
        };
    }

    public static void main(String[] args) {
        int[] muestras = {4, 9};
        List<Integer> valores = List.of(muestras[0], muestras[1]);
        Integer opcional = null;
        Estado estado = new Activo("Ada", valores.get(1));

        System.out.println(resumen(estado));
        System.out.println("array=" + muestras.length + ", valores=" + valores);
        System.out.println("Integer nulo=" + (opcional == null));
    }
}
```

Comandos orientativos en un JDK compatible:

```bash
javac --release 21 TiposDemo.java
java TiposDemo
```

Salida esperada:

```text
Ada: 9
array=2, valores=[4, 9]
Integer nulo=true
```

`Estado` es referencia sellada y cubre dos records; el `switch` descompone cada record con record patterns. `var` en `Activo(var nombre, var puntos)` infiere tipos de componentes del patrón, no declara variables dinámicamente tipadas. `muestras` es array de primitivas; crear `List<Integer>` requiere wrappers y `List.of` fija una lista no modificable. `opcional` aquí es una referencia `Integer` nula para mostrar comprobación explícita; una API pública donde la ausencia sea parte del contrato podría preferir `Optional<Integer>` [35] [41] [42] [43].

> **Verificación de ejemplo.** No se ha ejecutado este programa ni se han comprobado sus salidas con `javac` en el entorno de redacción. Las salidas anteriores se muestran como resultado esperado derivado del código; verifícalo en un JDK 21+ antes de incorporarlo a un flujo de producción.

### Errores frecuentes y recomendaciones profesionales

- **Confundir tipo estático y clase real.** El hecho de que una referencia apunte a una clase concreta no habilita todos sus métodos a través de un tipo estático más general. Declara el contrato que necesite el consumidor; usa patrón o cast comprobado cuando la lógica realmente dependa del subtipo.
- **Creer que todo `final` es inmutable.** `final` impide reasignar la variable, no modificar necesariamente el objeto. Emplea tipos inmutables, encapsulación y copias defensivas cuando la inmutabilidad sea un requisito.
- **Suponer que `char` siempre representa un carácter Unicode completo.** Es una unidad UTF-16. Para procesar texto Unicode más allá de BMP, trabaja con puntos de código mediante las API de `String`.
- **Ignorar promoción y narrowing.** `byte + byte` produce `int`; un cast no valida límites. Comprueba rango y usa conversiones de comprobación de desbordamiento cuando sean adecuadas.
- **Usar `==` para comparar objetos por contenido.** Para cadenas y wrappers, `==` prueba identidad; usa `equals` o comparación primitiva explícita. Para `null`, en cambio, `== null` es el test indicado.
- **Desenvolver wrappers nulos.** Antes de unboxing, valida o transforma el valor. Elige entre wrapper, primitiva, `Optional` u otro tipo explícito según si la ausencia sea válida.
- **Tratar genéricos como reificados.** `List<String>` no es distinguible en ejecución de `List<Integer>` como clase. Evita raw types, casts no comprobados y arreglos genéricos; respeta los warnings del compilador.
- **Usar `var` sin considerar el tipo inferido.** `var` mantiene tipado estático, pero puede hacer que una implementación concreta se filtre en el código local. Úsalo si mejora la claridad, no por obligación.
- **Asumir inmutabilidad profunda de record o lista no modificable.** Comprueba si los componentes son mutables y si se requieren copias defensivas.
- **Confundir preview con estable.** Los patrones primitivos en JDK 27 requieren habilitación preview y no son portables a todas las versiones. Fija el `--release` del proyecto y verifica que el JDK del compilador y del runtime coincidan con la característica requerida.

## 4. Fundamentos de programación

Esta sección concentra los conceptos que el temario base reúne bajo «Fundamentos de programación»: variables y constantes, operadores, decisiones, iteración, métodos, parámetros y argumentos, sobrecarga y varargs, `static`, ámbito, arrays y colecciones, excepciones, recursión, algoritmos y análisis Big-O. Java es de tipado estático: el tipo de cada variable y expresión se determina en compilación; las reglas de tipos y conversiones forman parte de la especificación del lenguaje [31].

#### Variables, asignación y convenciones para constantes

Una **variable** es un nombre declarado con un tipo que puede guardar un valor de ese tipo. En Java se declara antes de usarla; la asignación almacena el valor en una variable ya declarada, y `=` significa asignación, no una comparación. El tipo puede ser primitivo —por ejemplo `int`, `double` o `boolean`— o de referencia —por ejemplo `String`, un array o una colección—. Las variables locales deben recibir un valor antes de leerse; los campos de instancia y de clase reciben valores predeterminados si no tienen inicializador, como `0`, `false` o `null` según el tipo [31].

```java
int unidades = 3;
double precio = 12.50;
boolean disponible = true;
String producto = "cuaderno";
```

Los nombres de variables y métodos suelen escribirse en `lowerCamelCase` (`precioTotal`, `calcularImpuesto`); las clases, en `UpperCamelCase` (`CuentaBancaria`). Una constante de clase que se comparte y no debe reasignarse suele declararse `static final` y escribirse en `UPPER_SNAKE_CASE`, por ejemplo `static final int MAX_INTENTOS = 3`. Son convenciones de lectura, no una exigencia sintáctica del compilador. Las recomendaciones antiguas de Oracle sobre nombres son una referencia histórica y están expresamente archivadas; en un proyecto profesional conviene seguir el estilo vigente del repositorio [45].

`final` impide asignar otra vez una variable después de su inicialización, pero no hace inmutable el objeto al que apunta una referencia. Por ejemplo, una referencia `final` a una `ArrayList` no puede apuntar a otra lista, aunque el contenido de la lista siga siendo modificable. Una constante de compilación, en sentido estricto, es una variable `final` de tipo primitivo o `String` inicializada con una expresión constante; no toda variable `final` cumple esa condición [31].

**Errores frecuentes:** leer una variable local sin inicializar produce error de compilación; usar `==` para comparar el contenido de dos cadenas no es la forma correcta (véase «Operadores»); y asumir que `final` vuelve inmutable una colección confunde la referencia con el objeto. Inicializa las variables cerca del primer uso, escoge nombres descriptivos y usa `final` cuando el vínculo no deba reasignarse.

#### Operadores y expresiones

Un **operador** construye una expresión a partir de uno o más operandos. Los operadores aritméticos usuales son `+`, `-`, `*`, `/` y `%`; los relacionales son `<`, `<=`, `>`, `>=`, `==` y `!=`; los lógicos booleanos son `&&`, `||` y `!`. Java también ofrece operadores bit a bit (`&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`), asignaciones compuestas (`+=`, `-=`, entre otras), incremento y decremento (`++`, `--`) y el condicional ternario `condición ? valorSiCierto : valorSiFalso` [46].

```java
int total = 17;
int personas = 5;
System.out.println(total / personas); // 3: división entera, descarta la fracción
System.out.println(total % personas); // 2: resto
System.out.println(total >= 15 && personas > 0); // true
```

Cuando ambos operandos de `/` son enteros, el resultado también es entero y la parte fraccionaria se descarta hacia cero. Para división decimal, al menos un operando debe ser `double` o `float`, por ejemplo `(double) total / personas`. Los enteros `byte`, `short` y `char` se promueven normalmente a `int` en operaciones aritméticas. El desbordamiento de un entero no provoca por sí solo una excepción: el resultado sigue las reglas del tipo de ancho fijo; cuando el rango importa, usa comprobaciones o una API que detecte overflow. La división entera por cero sí lanza `ArithmeticException` [31] [46].

`&&` y `||` evalúan de izquierda a derecha y cortocircuitan: si el operando izquierdo basta para decidir el resultado, no evalúan el derecho. En expresiones booleanas, `&` y `|` evalúan ambos lados. Elige `&&` y `||` para condiciones normales; deja los operadores bit a bit para operaciones sobre bits. Los paréntesis ayudan a hacer explícito el orden cuando hay varios operadores.

Para primitivos, `==` compara valores. Para referencias, `==` compara si ambas referencias designan el mismo objeto. Para igualdad lógica entre cadenas usa `equals`, por ejemplo `"Java".equals(lenguaje)`. El operador `+` concatena si uno de los operandos es una cadena; evita construir texto repetidamente dentro de un bucle grande con concatenaciones ineficientes y considera `StringBuilder` cuando corresponda.

**Errores frecuentes:** escribir `=` en vez de `==` en una condición; dividir dos enteros esperando decimales; comparar cadenas con `==`; y escribir expresiones complejas sin paréntesis. Para dinero no uses `double` si la exactitud decimal es un requisito contable: considera `BigDecimal` y define deliberadamente la escala y el redondeo.

#### Condicionales y `switch`

`if` y `else if` permiten ejecutar una rama según una condición booleana; `else` cubre los demás casos. Las condiciones de Java deben ser `boolean`: no se acepta usar un número o una referencia directamente como condición, a diferencia de algunos otros lenguajes [47].

```java
int edad = 20;
if (edad >= 18) {
    System.out.println("Mayor de edad");
} else {
    System.out.println("Menor de edad");
}
```

`switch` selecciona entre varias alternativas. La forma tradicional con `case:` puede continuar a la siguiente etiqueta si no se ejecuta `break` (*fall-through*), lo que a veces es intencional pero es una fuente habitual de errores. Las reglas con flecha (`case ... ->`) no continúan implícitamente. Java también permite **expresiones `switch`**, que producen un valor; pueden agrupar etiquetas, usar `yield` en bloques y deben cubrir las alternativas posibles. La forma de expresión con flechas es estable desde Java 14; no requiere `--enable-preview` [47].

```java
int unidades = 3;
String categoria = switch (unidades) {
    case 1 -> "individual";
    case 2, 3 -> "pequeño";
    default -> "grande";
};
System.out.println(categoria);
```

En Java 21 se finalizaron las mejoras de patrones de `switch`; por tanto, patrones de tipo en `switch` no son preview en esa versión ni en las posteriores. No son necesarios en los ejemplos básicos de esta guía. La sintaxis exacta que admite un `switch` depende del tipo del selector y de las reglas de la versión objetivo [47].

**Errores frecuentes:** olvidar `break` en la forma con dos puntos cuando no se desea continuar; dejar un `switch` incompleto al añadir una nueva alternativa; y suponer que se puede seleccionar sobre cualquier tipo en cualquier versión. Para una enumeración, una expresión `switch` exhaustiva hace visible la falta de un caso cuando evoluciona el enum.

#### Bucles e iteraciones

Los bucles repiten una operación. `for` resulta útil cuando la inicialización, condición y actualización caben en una cabecera; `while` repite mientras se cumpla una condición; `do-while` ejecuta el cuerpo al menos una vez. El `for-each` (`for (Tipo elemento : colección)`) recorre elementos de un array o un objeto `Iterable` sin manipular manualmente un índice [47].

```java
int suma = 0;
for (int numero = 1; numero <= 4; numero++) {
    suma += numero;
}
System.out.println(suma); // 10
```

`break` termina el bucle más cercano; `continue` salta al siguiente ciclo del bucle más cercano. Usa etiquetas para saltos a bucles exteriores solo cuando simplifiquen claramente la lógica. En un `for-each`, no elimines elementos estructuralmente de una `ArrayList` directamente desde el cuerpo; usa el `Iterator` y su método `remove`, o un método de colección apropiado. Una condición que nunca cambia puede producir un bucle infinito; garantiza que cada repetición avance hacia la condición de salida.

Elige `for-each` si solo necesitas los valores. Usa un `for` con índice si el índice forma parte de la lógica o si necesitas actualizar posiciones en un array. Evita modificar el contador dentro del cuerpo sin motivo y evita bucles con efectos secundarios difíciles de seguir.

#### Métodos, funciones, parámetros y argumentos

En Java, el bloque reutilizable de código es un **método**: pertenece a una clase o a un objeto. No hay funciones o procedimientos independientes en el nivel superior de un archivo como abstracción ordinaria del lenguaje; un método declara un tipo de retorno (`int`, `String`, etc.) o `void` si no devuelve un resultado. Se lo invoca mediante su nombre y argumentos. La declaración determina el nombre, tipo de resultado y parámetros [48].

```java
static double calcularSubtotal(double precioUnitario, int unidades) {
    return precioUnitario * unidades;
}

// En otro método de la misma clase:
double subtotal = calcularSubtotal(12.5, 3);
```

Los **parámetros** son las variables declaradas en la definición (`precioUnitario`, `unidades`); los **argumentos** son los valores concretos pasados en la llamada (`12.5`, `3`). `return` devuelve un valor del tipo declarado y termina ese método. En un método `void`, se puede terminar con `return;`, pero no devolver un valor. Todos los argumentos de Java se pasan **por valor**: en un parámetro de referencia se copia el valor de la referencia, no se copia automáticamente el objeto. Por eso, un método puede mutar un objeto mutable recibido, pero reasignar el parámetro a otra referencia no cambia la variable del llamador [48].

Java no tiene una sintaxis especial de “parámetros nombrados”. La llamada se vincula por posición y por compatibilidad de tipos; nombres descriptivos de parámetros, objetos de configuración o constructores pueden hacer más legible una llamada larga. Divide métodos de acuerdo con una responsabilidad clara, y separa cálculo de entrada/salida cuando facilite probarlos.

#### Sobrecarga y argumentos variables (`varargs`)

La **sobrecarga** (*overloading*) permite declarar varios métodos del mismo nombre cuando sus listas de parámetros difieren en cantidad, tipos u orden. El compilador elige la sobrecarga aplicable usando los tipos estáticos de los argumentos y las reglas de resolución de llamadas. El tipo de retorno por sí solo no distingue una sobrecarga: no se pueden declarar dos métodos que solo difieran en el retorno [46] [48].

```java
static int sumar(int primero, int segundo) {
    return primero + segundo;
}

static int sumar(int... valores) {
    int total = 0;
    for (int valor : valores) {
        total += valor;
    }
    return total;
}
```

`int... valores` es un parámetro de aridad variable o *varargs*. En el cuerpo se trata como un array del tipo indicado. El parámetro varargs debe ser el último parámetro y solo puede existir uno por método; se puede invocar con cero o más argumentos de ese tipo, o pasar un array compatible. Una sobrecarga fija puede prevalecer sobre una varargs, por lo que procura evitar conjuntos de sobrecargas ambiguos. `sumar(2, 3)` selecciona la forma fija de dos parámetros; `sumar(1, 2, 3)` usa la varargs [48].

**Errores frecuentes:** intentar sobrecargar únicamente por el retorno; declarar parámetros después del varargs; y crear una ambigüedad con tipos relacionados, `null` o llamadas de cero argumentos. Mantén las sobrecargas semánticamente coherentes; si el conjunto confunde, cambia el nombre del método.

#### `static`: miembros de clase

Un campo o método `static` pertenece a la clase, no a cada instancia. Existe un campo de clase compartido por las instancias de esa clase cargada. Un método `static` puede invocarse mediante el nombre de la clase y no recibe un objeto `this`; por ello no puede acceder directamente a un campo o método de instancia que requiere un objeto concreto. Los métodos de instancia, por el contrario, operan sobre una instancia [48].

```java
final class Conversion {
    static final double CENTIMETROS_POR_PULGADA = 2.54;

    static double aCentimetros(double pulgadas) {
        return pulgadas * CENTIMETROS_POR_PULGADA;
    }
}

// Uso: Conversion.aCentimetros(2.0)
```

Usa `static` para operaciones sin estado por objeto y constantes compartidas; no lo conviertas en un almacén indiscriminado de estado mutable global. Un campo `static final` de tipo referencia fija la referencia, no garantiza la inmutabilidad del objeto. `static` tampoco significa que el valor persista después de que termine el proceso, ni que sea seguro para concurrencia por sí solo.

#### Ámbito (`scope`) y ciclo de vida de nombres

El **ámbito** es la región del código en la que una declaración puede referirse mediante su nombre, sujeto a ocultación por otra declaración. Los parámetros viven durante la invocación del método; una variable local declarada dentro de un bloque solo se puede usar dentro de ese ámbito; los campos son miembros de la clase y su acceso depende además de modificadores como `private` o `public`. Ámbito y tiempo de vida no son sinónimos: que un nombre deje de estar disponible no implica necesariamente que el objeto referenciado sea destruido en ese instante [49].

```java
class Ambito {
    private int cantidad = 10; // campo de instancia

    void mostrar(int cantidad) { // el parámetro oculta el campo en este método
        int doble = cantidad * 2; // variable local
        System.out.println(doble);
        System.out.println(this.cantidad); // acceso explícito al campo
    }
}
```

`this.cantidad` identifica el campo ocultado por el parámetro homónimo. Es preferible no reutilizar nombres que obliguen a desambiguar sin necesidad. Los bloques (`{ ... }`) delimitan ámbitos locales, y las variables locales deben estar definitivamente asignadas antes de leerse; esta regla se verifica en compilación [31] [49].

#### Arrays y colecciones básicas

Un **array** almacena una cantidad fija de componentes del mismo tipo. Es un objeto, los índices comienzan en cero y su longitud se obtiene con `.length`. Los arrays pueden contener tipos primitivos (`int[]`) o referencias (`String[]`). La longitud no cambia una vez creado el array; acceder a un índice fuera de rango produce `ArrayIndexOutOfBoundsException` [34].

```java
int[] notas = {8, 10, 9};
System.out.println(notas[0]);     // 8
System.out.println(notas.length); // 3
```

Las **colecciones** de `java.util` ofrecen estructuras redimensionables y contratos comunes. Las interfaces más usadas son `List<E>` para una secuencia con orden e índices, `Set<E>` para elementos únicos, `Map<K,V>` para pares clave-valor, y `Queue<E>`/`Deque<E>` para colas y dobles extremos. Por ejemplo, `ArrayList<E>` implementa una lista redimensionable; `HashSet<E>` y `HashMap<K,V>` están basados en tablas hash. Los genéricos se escriben con tipos de referencia (`List<Integer>`, no `List<int>`); el autoboxing convierte entre primitivos y sus envoltorios, como `int` e `Integer` [50].

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.HashSet;
import java.util.List;
import java.util.Map;
import java.util.Set;

List<String> nombres = new ArrayList<>();
nombres.add("Ada");
nombres.add("Linus");
Set<Integer> codigos = new HashSet<>(List.of(7, 7, 9));
Map<String, Integer> puntuaciones = new HashMap<>();
puntuaciones.put("Ada", 10);
```

No todas las estructuras son tipos integrados del lenguaje: las interfaces y clases citadas pertenecen a la biblioteca estándar. Un array es preferible cuando el tamaño es fijo o se necesita una representación sencilla; una `List` cuando la secuencia crece o se reduce. Para una pila o cola de propósito general, `Deque` con `ArrayDeque` suele ser una opción apropiada; `ArrayDeque` no admite elementos `null`. `List.of(...)` crea una lista no modificable, no una lista a la que se pueda añadir elementos; usa `new ArrayList<>(List.of(...))` si necesitas una copia modificable [50] [51].

Los costes dependen de la implementación. En `ArrayList`, acceso por índice y `size()` son O(1), `add` al final es O(1) amortizado y otras operaciones que desplazan o buscan elementos suelen ser O(n). `HashMap` ofrece O(1) para operaciones básicas bajo dispersión adecuada de hashes; no es una garantía para cualquier distribución. `HashSet` comparte la condición para sus operaciones básicas, y no garantiza orden de iteración. Estas características describen las implementaciones de la API indicada, no una promesa universal de toda colección o cualquier implementación [52] [53] [54].

**Errores frecuentes:** confundir `.length` del array con `size()` de una colección; usar índices que empiezan en uno; intentar añadir en una lista creada con `List.of`; esperar orden en `HashSet` o `HashMap`; y usar `==` para comparar el contenido de objetos. En producción, programa contra interfaces (`List`, `Set`, `Map`) cuando no necesites una implementación concreta.

#### Excepciones y tratamiento de errores

Una excepción representa una condición que interrumpe el flujo normal. En Java, todos los objetos lanzables derivan de `Throwable`; sus ramas principales son `Error` y `Exception`. Las excepciones **comprobadas** (*checked*) deben capturarse o declararse en `throws`; `RuntimeException` y `Error` son no comprobadas. Un error de compilación se informa antes de ejecutar; una excepción de ejecución aparece durante el programa; un error lógico puede producir una salida incorrecta sin lanzar excepción [55] [56].

```java
try {
    int cantidad = Integer.parseInt("no-es-un-entero");
    System.out.println(cantidad);
} catch (NumberFormatException error) {
    System.out.println("La entrada debe ser un entero");
}
```

`try` delimita la operación; `catch` debe capturar un tipo que se pueda tratar; `finally` permite limpieza que deba ocurrir tanto si la operación termina bien como si falla. Para recursos que implementan `AutoCloseable`, prefiere `try`-con-recursos, que cierra automáticamente el recurso. Propaga o transforma una excepción con contexto cuando el método no puede resolverla, y conserva la causa al envolverla. Captura excepciones específicas; `catch (Exception)` indiscriminado, silenciar errores o usar excepciones como flujo normal dificulta el diagnóstico [55] [56].

**Errores frecuentes:** capturar `Exception` y no hacer nada; capturar una excepción y continuar con un estado inválido; confundir `throw` (lanza un objeto) con `throws` (declara excepciones posibles); y olvidar cerrar un recurso. Valida datos en los límites del programa y elige excepciones para comunicar fallos recuperables, no como sustituto de condiciones ordinarias.

#### Recursión

Una función recursiva se expresa en Java como un método que se llama a sí mismo. Necesita un **caso base**, que detiene la cadena de llamadas, y un paso recursivo que acerque la entrada al caso base. Cada llamada ocupa recursos de ejecución; una recursión demasiado profunda puede terminar en `StackOverflowError`. Java no promete optimización de llamadas de cola, así que no supongas que la recursión profunda se convertirá automáticamente en un bucle [48] [55].

```java
static long factorial(int n) {
    if (n < 0) {
        throw new IllegalArgumentException("n debe ser no negativo");
    }
    if (n <= 1) {
        return 1;
    }
    return n * factorial(n - 1);
}
```

Para `factorial(5)`, las llamadas reducen `5` a `4`, `3`, `2` y `1`; el caso base devuelve `1` y las llamadas pendientes producen `120`. Este algoritmo es didáctico: el factorial crece deprisa, y `long` desborda para valores relativamente pequeños. Para entradas grandes o no acotadas, usa una estrategia iterativa, comprueba los límites o elige una representación numérica adecuada.

**Errores frecuentes:** olvidar el caso base; no reducir la entrada; aceptar una entrada inválida que recursa indefinidamente; y no considerar desbordamiento o profundidad. Antes de elegir recursión, comprueba si hace el algoritmo más claro y si la profundidad máxima está acotada.

#### Algoritmos y complejidad Big-O

Un **algoritmo** es una secuencia finita y precisa de pasos que resuelve un problema. La complejidad temporal estima cómo crece el trabajo cuando aumenta el tamaño de entrada `n`; la espacial estima el crecimiento de memoria adicional. La notación **Big-O** describe una cota de crecimiento asintótico, dejando de lado constantes y términos de menor orden: no indica segundos de ejecución y no sustituye la medición [52] [53] [54].

| Complejidad | Crecimiento típico | Ejemplo intuitivo |
|---|---|---|
| O(1) | constante | Leer un elemento de `array[i]`. |
| O(log n) | logarítmico | Búsqueda binaria sobre datos ordenados. |
| O(n) | lineal | Recorrer una colección una vez. |
| O(n log n) | cuasilineal | Ordenación eficiente por comparación. |
| O(n²) | cuadrático | Comparar cada elemento con cada otro mediante dos bucles. |

El fragmento siguiente detecta si hay un duplicado. La versión anidada puede comparar un número proporcional a `n²` de pares y usa O(1) de memoria adicional; la versión con `HashSet` realiza una pasada, necesita hasta O(n) memoria y suele ser O(n) en tiempo esperado cuando las operaciones hash se dispersan correctamente. El peor comportamiento depende de las claves, la distribución de `hashCode()` y la implementación; no presentes el promedio de una tabla hash como garantía de peor caso [53] [54].

```java
static boolean hayDuplicadoLento(int[] valores) {
    for (int i = 0; i < valores.length; i++) {
        for (int j = i + 1; j < valores.length; j++) {
            if (valores[i] == valores[j]) {
                return true;
            }
        }
    }
    return false;
}

static boolean hayDuplicadoRapido(int[] valores) {
    Set<Integer> vistos = new HashSet<>();
    for (int valor : valores) {
        if (!vistos.add(valor)) {
            return true;
        }
    }
    return false;
}
```

Ambos algoritmos responden `true` para `{4, 7, 4}`. El segundo no es «mejor» en todo caso: intercambia memoria por tiempo esperado, y para entradas muy pequeñas la diferencia puede ser irrelevante. Analiza restricciones, elige una estructura cuyo contrato se ajuste a las operaciones necesarias y perfila antes de optimizar.

#### Ejemplo progresivo completo y ejecutable

El siguiente programa reúne declaraciones, constante, operadores, `if`, expresión `switch`, bucles, métodos, sobrecarga, varargs, miembro `static`, alcance, arrays, colecciones, excepción, recursión y búsqueda de duplicados. No requiere dependencias externas ni características preview.

Guárdalo como `FundamentosJava.java` y ejecuta desde esa carpeta:

```bash
javac FundamentosJava.java
java FundamentosJava
```

En un JDK 11 o posterior también se puede usar el modo de archivo fuente con `java FundamentosJava.java`; esa forma compila en memoria y ejecuta el archivo sin dejar el `.class` habitual [29]. Para un proyecto, conserva el flujo `javac`/`java` o el sistema de construcción que haya adoptado el repositorio.

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.HashSet;
import java.util.List;
import java.util.Map;
import java.util.Set;

public class FundamentosJava {
    private static final double TASA_IMPUESTO = 0.10;
    private static String etiqueta = "campo de clase";

    public static void main(String[] args) {
        final int unidades = 3;
        double precioUnitario = 12.5;
        double subtotal = calcularSubtotal(precioUnitario, unidades);
        System.out.println("Subtotal: " + subtotal);
        System.out.println("Con impuesto: " + (subtotal * (1 + TASA_IMPUESTO)));

        if (subtotal >= 30) {
            System.out.println("Descuento: aplicable");
        } else {
            System.out.println("Descuento: no aplicable");
        }

        String categoria = switch (unidades) {
            case 1 -> "individual";
            case 2, 3 -> "pequeño";
            default -> "grande";
        };
        System.out.println("Categoría: " + categoria);

        int suma = 0;
        for (int numero = 1; numero <= 4; numero++) {
            suma += numero;
        }
        int cuentaRegresiva = 2;
        while (cuentaRegresiva > 0) {
            cuentaRegresiva--;
        }
        System.out.println("Suma del 1 al 4: " + suma);

        int[] notas = {8, 10, 9};
        List<String> nombres = new ArrayList<>(List.of("Ada", "Linus"));
        nombres.add("Grace");
        Set<Integer> codigos = new HashSet<>(List.of(7, 7, 9));
        Map<String, Integer> puntuaciones = new HashMap<>();
        puntuaciones.put("Ada", 10);
        System.out.println("Array: " + notas[0] + ", longitud=" + notas.length);
        System.out.println("Lista: " + nombres);
        System.out.println("Códigos únicos: " + codigos.size());
        System.out.println("Puntuación de Ada: " + puntuaciones.get("Ada"));

        System.out.println("sumar(2, 3): " + sumar(2, 3));
        System.out.println("sumar(1, 2, 3): " + sumar(1, 2, 3));
        System.out.println("Factorial de 5: " + factorial(5));
        System.out.println("Duplicado: " + hayDuplicadoRapido(new int[]{4, 7, 4}));
        mostrarAmbito();

        try {
            Integer.parseInt("doce");
        } catch (NumberFormatException error) {
            System.out.println("Entrada inválida: se esperaba un entero");
        }
    }

    static double calcularSubtotal(double precio, int cantidad) {
        return precio * cantidad;
    }

    static int sumar(int primero, int segundo) {
        return primero + segundo;
    }

    static int sumar(int... valores) {
        int total = 0;
        for (int valor : valores) {
            total += valor;
        }
        return total;
    }

    static long factorial(int n) {
        if (n < 0) {
            throw new IllegalArgumentException("n debe ser no negativo");
        }
        if (n <= 1) {
            return 1;
        }
        return n * factorial(n - 1);
    }

    static boolean hayDuplicadoRapido(int[] valores) {
        Set<Integer> vistos = new HashSet<>();
        for (int valor : valores) {
            if (!vistos.add(valor)) {
                return true;
            }
        }
        return false;
    }

    static void mostrarAmbito() {
        String etiqueta = "variable local";
        System.out.println("Ámbito local: " + etiqueta);
        System.out.println("Ámbito de clase: " + FundamentosJava.etiqueta);
    }
}
```

**Salida esperada:**

```text
Subtotal: 37.5
Con impuesto: 41.25
Descuento: aplicable
Categoría: pequeño
Suma del 1 al 4: 10
Array: 8, longitud=3
Lista: [Ada, Linus, Grace]
Códigos únicos: 2
Puntuación de Ada: 10
sumar(2, 3): 5
sumar(1, 2, 3): 6
Factorial de 5: 120
Duplicado: true
Ámbito local: variable local
Ámbito de clase: campo de clase
Entrada inválida: se esperaba un entero
```

La sobrecarga `sumar(int, int)` muestra la llamada de aridad fija; la forma `sumar(int...)` recibe tres valores como un array. `HashSet` elimina el código repetido, y se imprime su cantidad, no el orden de iteración. La conversión inválida produce `NumberFormatException`, que el bloque captura de manera específica. El contador del `while` se decrementa hasta que deja de cumplirse la condición.

La muestra fue compilada y ejecutada con OpenJDK 21.0.13.1 en el entorno indicado; la salida mostrada coincide con esa ejecución. No se ha ejecutado con JDK 25 ni JDK 27 en este entorno. La sintaxis del código es estable y sus APIs son anteriores a Java 17, pero un programa real debe compilarse y probarse con el proveedor, versión y sistema operativo de destino.

#### Errores frecuentes y recomendaciones de síntesis

- **No inicializar una variable local:** el compilador impide leerla hasta que puede demostrar que recibió valor en todos los caminos posibles. Asigna el valor inicial apropiado, no un valor ficticio para silenciar el error.
- **Confundir identidad con igualdad:** usa `==` para primitivos y comparaciones de identidad intencionales; usa `equals` para el contenido de cadenas y objetos. Algunas clases requieren implementar coherentemente `equals` y `hashCode` para funcionar como claves de mapas o miembros de conjuntos.
- **Mezclar división entera y decimal:** convierte uno de los operandos antes de dividir si necesitas precisión fraccionaria; evita una conversión después de que ya se perdió la fracción.
- **Crear `switch` o bucles frágiles:** considera las ramas faltantes, el `fall-through`, índices desde cero, límites de iteración y la condición de salida. Elige la construcción más directa.
- **Diseñar métodos demasiado grandes o con efectos ocultos:** usa parámetros y resultados explícitos; limita estado `static` mutable; elige nombres que expresen intención.
- **Tratar arrays y colecciones como intercambiables:** los arrays tienen longitud fija y `.length`; las colecciones tienen operaciones definidas por sus interfaces, como `size()`, `add` y `remove`.
- **Usar excepciones para cualquier condición:** valida entradas, captura el tipo que puede manejarse y no escondas la causa del fallo. Para cerrar recursos, prefiere *try-with-resources*.
- **Llamar recursivamente sin analizar límites:** prueba los casos mínimo y límite, y usa iteración si la profundidad puede crecer con datos externos.
- **Leer Big-O como tiempo real o garantía universal:** la notación modela crecimiento; los costes concretos dependen del algoritmo, la estructura, los datos, el JDK, el hardware y el entorno. Distingue el caso esperado del peor caso y la memoria adicional del total de memoria.

Para practicar, cambia las unidades del programa y predice la salida antes de ejecutarlo; agrega una alternativa a `switch`; implementa una búsqueda lineal; compara la versión cuadrática y la versión con conjunto para duplicados; y modifica `factorial` para que sea iterativo. Para cada cambio, comprueba casos normales, límites y entradas inválidas. La progresión útil es comprender el contrato, razonar sobre el estado y el resultado, probarlo, y recién entonces optimizarlo.

## 5. Estructuras de datos

**Versión documental:** Java SE 27, con distinción explícita frente a Java 25 LTS.  
**Fecha de corte:** 18 de noviembre de 2026.  
**Nivel:** progresivo, de fundamentos a selección profesional.  
**Alcance:** arrays y colecciones Java, complejidad, contratos de igualdad y selección; no desarrolla los otros temas de la guía.

Al 18 de noviembre de 2026, JDK 27 es la versión GA más reciente de Java SE; Oracle publicó JDK 27.0.1.1 el 17 de noviembre. JDK 25 es la LTS más reciente. Java 27 es una versión no LTS y el roadmap de Oracle señala Java 29 como la siguiente LTS planificada para septiembre de 2027; ese calendario puede cambiar [57] [3]. Las APIs aquí citadas corresponden a Java SE 27. Salvo donde se indica, los ejemplos usan APIs estables, sin características *preview* ni *incubator*.

La salida del programa completo de esta sección se comprobó con OpenJDK 21.0.13.1 en Linux, no con JDK 27. Las líneas de código y salidas indicadas son las verificadas en ese entorno. Para reproducirlas, guarda el ejemplo como `EstructurasDemo.java` y ejecuta `javac EstructurasDemo.java && java EstructurasDemo`. La sintaxis usada es compatible con Java 21; los métodos de colecciones secuenciadas del ejemplo requieren Java 21 o posterior. No debe inferirse de esta comprobación un benchmark o el mismo rendimiento en otro JDK, JVM, proveedor o sistema operativo.

#### Modelo mental: interfaz y clase de implementación

Una **estructura de datos** organiza valores y define cómo acceder a ellos, añadirlos, buscarlos o eliminarlos. Una **interfaz** expresa operaciones y contratos sin exigir una representación concreta; una **clase** implementa esos contratos usando alguna representación interna. Esta separación permite programar contra el comportamiento requerido y cambiar la implementación cuando los requisitos de orden, coste o mutabilidad cambian [58].

En el Java Collections Framework, `Collection<E>` es la raíz de la jerarquía de colecciones; `List<E>`, `Set<E>`, `Queue<E>` y `Deque<E>` son interfaces. `ArrayList<E>`, `LinkedList<E>`, `HashSet<E>`, `TreeSet<E>`, `HashMap<K,V>`, `TreeMap<K,V>`, `ArrayDeque<E>` y `PriorityQueue<E>` son clases concretas. `Map<K,V>` es una interfaz separada: no extiende `Collection`, porque representa asociaciones clave-valor, no una secuencia de elementos [58] [59].

El tipo declarado normalmente expresa el contrato que necesita el algoritmo; la clase creada elige una representación:

```java
List<String> nombres = new ArrayList<>();
Set<String> unicos = new HashSet<>();
Map<String, Integer> edades = new HashMap<>();
Deque<String> pendientes = new ArrayDeque<>();
```

`ArrayList` permite operaciones propias como `ensureCapacity`, pero la mayoría de los algoritmos solo necesitan `List`. Si una operación particular exige `firstKey()`, se debe declarar o convertir la referencia a un tipo de mapa ordenado, como `TreeMap` o `NavigableMap`; el método no pertenece a `Map`.

#### Arrays

Un **array** es un objeto de longitud fija cuyos componentes tienen todos el mismo tipo. Su tamaño se decide al crearlo y queda fijado; para crecer, se crea otro array y se copian elementos. Los índices empiezan en cero y `array.length` indica el número de posiciones. El acceso por índice es una operación directa de la estructura, normalmente descrita como O(1). Un índice menor que cero o igual o mayor que `length` provoca `ArrayIndexOutOfBoundsException` [34].

Java admite arrays de tipos primitivos (`int[]`, `double[]`) y de referencias (`String[]`, `Pedido[]`). Un array de referencias puede contener `null`; un array primitivo comienza con el valor por defecto del tipo. Arrays de referencias son covariantes: un `String[]` puede asignarse a una variable `Object[]`, pero insertar en ella un objeto incompatible con el tipo real provoca `ArrayStoreException`. Los arrays genéricos parametrizados no se crean directamente (`new List<String>[60]` no compila), debido a que los argumentos genéricos no están reificados como el tipo de componente del array [34] [31].

```java
int[] puntuaciones = {8, 10, 7};
puntuaciones[1] = 9;
System.out.println(puntuaciones.length);
System.out.println(puntuaciones[1]);
```

Salida esperada:

```text
3
9
```

Los arrays multidimensionales son arrays cuyos componentes pueden ser otros arrays. Por eso pueden ser irregulares: cada fila puede tener longitud diferente. La clase utilitaria `java.util.Arrays` proporciona operaciones como `sort`, `binarySearch`, `equals`, `fill`, `copyOf` y `toString`; `binarySearch` requiere que el array o rango esté ordenado de acuerdo con el mismo criterio [61].

```java
import java.util.Arrays;

int[] valores = {12, 3, 8};
Arrays.sort(valores);
int indice = Arrays.binarySearch(valores, 8);
System.out.println(Arrays.toString(valores));
System.out.println("índice de 8=" + indice);
```

Salida esperada:

```text
[3, 8, 12]
índice de 8=1
```

No se debe tratar `Arrays.asList(array)` como una copia dinámica: devuelve una lista de tamaño fijo respaldada por el array. Cambiar una posición de la lista modifica el array y `add`/`remove` no están disponibles. Con un array primitivo como `int[]`, la llamada `Arrays.asList(intArray)` produce una lista con un elemento de tipo `int[]`, no una lista de enteros. Para una lista dinámica, copia o añade elementos a un `ArrayList` [61].

#### List, ArrayList y LinkedList

`List<E>` representa una colección ordenada por posiciones, con acceso mediante índices y, normalmente, elementos repetidos. La interfaz define qué operaciones están disponibles (`get`, `set`, `add`, `remove`, iteradores), pero no garantiza que cada operación tenga igual coste en todas sus implementaciones [62]. Los genéricos de las colecciones admiten tipos de referencia: para números se escribe `List<Integer>`, no `List<int>`. La conversión automática entre `int` e `Integer` se llama *boxing* y puede crear objetos adicionales.

`ArrayList<E>` es la implementación habitual para una secuencia redimensionable. Su API documenta tiempo constante para `get` y `set`, tiempo constante amortizado al añadir al final y tiempo lineal aproximado para las demás operaciones. Insertar o quitar en el medio desplaza referencias posteriores; buscar por valor recorre elementos. La capacidad interna puede aumentar al añadir, pero su política concreta de crecimiento no está especificada [52].

```java
List<String> tareas = new ArrayList<>();
tareas.add("leer");
tareas.add("probar");
tareas.add(1, "compilar");
String primera = tareas.get(0);
tareas.set(0, "repasar");
System.out.println(tareas);
System.out.println(primera);
```

Salida esperada:

```text
[repasar, compilar, probar]
leer
```

`LinkedList<E>` es una clase de lista doblemente enlazada que también implementa `Deque<E>`. Es útil si se necesitan las operaciones de ambos extremos de la lista; no proporciona acceso directo por índice. Para `get(i)` u otra operación indexada debe recorrer desde uno de los extremos hasta la posición, de modo que repetir `get(i)` en un bucle puede convertir un recorrido lineal en O(n²). Para acceso aleatorio e iteración secuencial general, `ArrayList` suele ser una mejor elección; para una pila o cola habitual, `ArrayDeque` suele ser preferible a `LinkedList` [60] [63] [51].

Una lista creada con `List.of(...)` es **no modificable**: no permite añadir, quitar ni reemplazar elementos y rechaza `null`. Una vista no modificable no hace inmutables los objetos que contiene. `Arrays.asList(...)`, en cambio, permite reemplazar posiciones con `set`, pero no cambiar el tamaño. Comprueba el contrato de mutabilidad de la fábrica usada antes de llamar a un método modificador [62].

Java no ofrece un tipo general de **tupla** de longitud arbitraria en la biblioteca estándar. Si el grupo de valores tiene significado y campos identificables, un `record` es una alternativa con nombres (`record Punto(int x, int y) {}`). `Map.Entry<K,V>` representa un par clave-valor en el contexto de un mapa; no convierte las listas en tuplas [59].

#### Set y conjuntos

`Set<E>` es una interfaz para colecciones que no contienen dos elementos iguales según `equals`. El contrato no promete por sí solo un orden de iteración. Entre las implementaciones estándar, `HashSet<E>` usa una tabla hash y permite un elemento `null`; ofrece coste constante esperado para operaciones básicas como `add`, `remove` y `contains`, bajo una distribución adecuada de códigos hash. Su iteración cuesta proporcionalmente al número de elementos más la capacidad de su tabla; el orden no está garantizado [64] [54].

`TreeSet<E>` mantiene los elementos ordenados por su orden natural (`Comparable`) o por un `Comparator`. Sus operaciones básicas de pertenencia, alta y baja tienen coste garantizado O(log n). La comparación que devuelve cero define cuándo el conjunto considera dos elementos equivalentes; idealmente, ese criterio debe ser consistente con `equals` para respetar el contrato de `Set` [65]. Si solo se requiere preservar el orden de inserción, `LinkedHashSet` es una alternativa estándar: ese requisito es distinto del ordenamiento por comparación.

```java
Set<String> lenguajes = new HashSet<>();
lenguajes.add("Java");
lenguajes.add("Java");
System.out.println("cantidad=" + lenguajes.size());
System.out.println("contiene=" + lenguajes.contains("Java"));

Set<Integer> ordenados = new java.util.TreeSet<>(List.of(9, 2, 5));
System.out.println(ordenados);
```

Salida esperada:

```text
cantidad=1
contiene=true
[2, 5, 9]
```

La salida del `HashSet` no se debe interpretar como un orden estable. El ejemplo imprime solo su tamaño y pertenencia; el `TreeSet` sí muestra los elementos ordenados. Si se necesita un conjunto no modificable, `Set.of(...)` lo crea, pero no admite `null` ni elementos repetidos en los argumentos [64] [65].

#### Map, HashMap y TreeMap

`Map<K,V>` relaciona una clave única con un valor. Puede consultar o sustituir el valor asociado a una clave, y exponer vistas de claves, valores y pares mediante `keySet()`, `values()` y `entrySet()`. Los valores sí pueden repetirse. El orden depende de la implementación; no hay que asumirlo por el mero hecho de recorrer el mapa [59] [53].

`HashMap<K,V>` implementa `Map` con una tabla hash, permite una clave `null` y valores `null`, y no garantiza orden. Sus operaciones básicas `get` y `put` tienen coste constante esperado si el hash distribuye bien las claves. Una colisión elevada puede perjudicar el rendimiento; iterar las vistas cuesta O(capacidad + tamaño), por lo que una capacidad inicial excesiva también tiene coste [53]. `get(key) == null` no distingue por sí solo entre clave ausente y clave asociada explícitamente a `null`; se puede comprobar con `containsKey`.

`TreeMap<K,V>` implementa un mapa ordenado y navegable basado en un árbol rojo-negro. Ordena las claves por `Comparable` o un `Comparator`; `get`, `put`, `remove` y `containsKey` tienen coste garantizado O(log n). Ofrece operaciones de navegación y vistas por rangos. Si el comparador trata dos claves como iguales (`compare(a,b) == 0`), el mapa las considera la misma posición; conviene que este orden sea consistente con `equals` [66] [67].

```java
Map<String, Integer> conteos = new HashMap<>();
conteos.merge("rojo", 1, Integer::sum);
conteos.merge("azul", 1, Integer::sum);
conteos.merge("rojo", 1, Integer::sum);
System.out.println("rojo=" + conteos.get("rojo"));
System.out.println("hay verde=" + conteos.containsKey("verde"));

TreeMap<String, Integer> puntuaciones = new TreeMap<>();
puntuaciones.put("Marta", 91);
puntuaciones.put("Ana", 95);
System.out.println("primera clave=" + puntuaciones.firstKey());
```

Salida esperada:

```text
rojo=2
hay verde=false
primera clave=Ana
```

`Map.of(...)` y `Map.copyOf(...)` crean mapas no modificables que rechazan claves y valores `null`; no son sinónimos de `HashMap` mutable. Los mapas mutables tampoco deben modificarse indirectamente mediante una clave después de insertarla si esa modificación cambia su `equals` o `hashCode` [59] [53].

#### Contrato de equals y hashCode

`Object.equals(Object)` define igualdad lógica; su contrato exige reflexividad, simetría, transitividad y consistencia mientras no cambien los datos usados por la comparación. `hashCode()` produce un entero útil para tablas hash. La regla central es: si `a.equals(b)` es `true`, entonces `a.hashCode() == b.hashCode()` debe ser verdadero. Lo inverso no se exige: dos objetos desiguales pueden tener el mismo hash, lo que se denomina colisión [68].

Si una clase redefine `equals`, normalmente debe redefinir también `hashCode`. De otro modo, un `HashSet` puede guardar dos instancias que la aplicación considera iguales o un `HashMap` no encontrar una clave equivalente. No uses campos mutables de igualdad/hash en claves mientras estén almacenadas en mapas o conjuntos hash. En estructuras ordenadas, aplica la misma atención a `compareTo` o `Comparator` [54] [53] [66] [68].

```java
import java.util.Objects;

final class Codigo {
    private final String valor;

    Codigo(String valor) {
        this.valor = Objects.requireNonNull(valor);
    }

    @Override
    public boolean equals(Object objeto) {
        if (this == objeto) return true;
        if (!(objeto instanceof Codigo otro)) return false;
        return valor.equals(otro.valor);
    }

    @Override
    public int hashCode() {
        return Objects.hash(valor);
    }
}
```

La clase es `final`, mantiene su dato inmutable y calcula tanto igualdad como hash a partir del mismo campo. En clases con herencia, la igualdad requiere un diseño deliberado para no romper simetría; los `record` generan automáticamente igualdad y hash basados en sus componentes, lo que puede evitar código repetitivo cuando esa semántica coincide con el dominio.

#### Pilas, colas y ArrayDeque

Una **pila** es LIFO: el último elemento añadido es el primero que se retira. Una **cola** FIFO retira primero el elemento que lleva más tiempo esperando. `Deque<E>` es una interfaz de doble extremo que permite añadir, examinar y quitar en ambos extremos; puede representar ambas abstracciones. `ArrayDeque<E>` es su implementación de array redimensionable. La documentación indica tiempo amortizado constante para la mayoría de sus operaciones; búsquedas y eliminación de una ocurrencia interior son lineales. No admite `null` ni es segura para acceso concurrente sin sincronización [63] [51].

Para pila, el patrón `Deque<T> pila = new ArrayDeque<>();` usa `push`, `pop` y `peek`, que actúan en la cabecera. Para cola, `offerLast` añade al final y `pollFirst` retira del comienzo; `peekFirst` consulta el próximo elemento sin quitarlo. `poll`/`peek` devuelven `null` cuando no hay elemento, mientras que `remove`/`element` lanzan una excepción si está vacía. Como `ArrayDeque` prohíbe `null`, el resultado `null` de `poll` puede señalar cola vacía [63] [51].

La clase antigua `Stack<E>` existe por compatibilidad, pero la documentación recomienda preferir `Deque` y sus implementaciones. `ArrayDeque` es una opción normal para una pila o cola local; si varios hilos deben coordinarse, selecciona una implementación concurrente adecuada en vez de suponer que la clase es segura entre hilos [63] [51] [69].

#### PriorityQueue

`PriorityQueue<E>` es una cola de prioridad basada en heap. `peek()` devuelve el elemento mínimo según el orden natural o el `Comparator` suministrado; no se comporta como FIFO, y los empates no tienen orden estable. `offer`/`add` y `poll`/`remove()` tienen coste O(log n); `peek`, `element` y `size` son O(1); `contains` y `remove(Object)` son O(n). El iterador no recorre los elementos en orden de prioridad. Para extraerlos ordenadamente, repite `poll` sobre una copia o vacía la cola [70].

```java
PriorityQueue<Integer> trabajos = new PriorityQueue<>();
trabajos.addAll(List.of(5, 1, 3));
System.out.println(trabajos.peek());
while (!trabajos.isEmpty()) {
    System.out.print(trabajos.poll() + " ");
}
```

Salida esperada:

```text
1
1 3 5 
```

Para prioridad inversa, se puede suministrar `Comparator.reverseOrder()`. Los elementos deben ser comparables entre sí según el criterio; `PriorityQueue` no admite `null`. Si la semántica exige FIFO entre prioridades iguales, añade explícitamente un número de secuencia como desempate al comparador [70].

#### Listas enlazadas, árboles y grafos

Una lista enlazada puede describirse con nodos que guardan un valor y referencias a nodos vecinos. Java sí incluye `LinkedList`, una lista doblemente enlazada de uso general, pero no un tipo separado de nodo `LinkedListNode` para construir cualquier cadena propia. Implementar nodos propios puede ser útil para aprender algoritmos o para una representación especializada; en producción suele ser mejor comenzar por `ArrayList`, `LinkedList` o `ArrayDeque` y justificar cualquier estructura personalizada con requisitos medibles [60].

Java tampoco ofrece una interfaz universal de árbol binario de búsqueda, AVL o B-tree en `java.util`. `TreeMap` y `TreeSet` son colecciones ordenadas implementadas con árboles rojo-negro, pero son mapas y conjuntos, no una API general para modelar cualquier árbol. Un árbol de dominio se puede representar con clases de nodos propias; al hacerlo, hay que definir invariantes, recorridos, balanceo, reglas de duplicados y pruebas. Una clase didáctica sin balanceo puede degradarse de O(log n) a O(n) en operaciones de búsqueda según la forma del árbol.

Un **grafo** modela vértices y aristas dirigidas o no dirigidas. No hay una estructura de grafo general incorporada en la biblioteca estándar. Para un grafo disperso y sencillo, una representación de adyacencia como `Map<V, List<V>>` es suficiente; un `Set<V>` por vértice evita vecinos duplicados cuando eso sea parte del modelo. En un recorrido BFS con lista de adyacencia, una cola `ArrayDeque` y un conjunto de visitados, el coste es O(V + E) bajo las operaciones esperadas de hash, y el espacio adicional es O(V) [51] [71].

```java
Map<String, List<String>> grafo = new LinkedHashMap<>();
grafo.put("A", List.of("B", "C"));
grafo.put("B", List.of("D"));
grafo.put("C", List.of("D"));
grafo.put("D", List.of());

Deque<String> pendientes = new ArrayDeque<>();
Set<String> vistos = new HashSet<>();
List<String> recorrido = new ArrayList<>();
pendientes.addLast("A");
vistos.add("A");
while (!pendientes.isEmpty()) {
    String actual = pendientes.removeFirst();
    recorrido.add(actual);
    for (String vecino : grafo.getOrDefault(actual, List.of())) {
        if (vistos.add(vecino)) pendientes.addLast(vecino);
    }
}
System.out.println(recorrido);
```

Salida esperada: `[A, B, C, D]`. `LinkedHashMap` y las listas del ejemplo conservan un orden de recorrido concreto; BFS no promete un orden universal entre vecinos si la representación de adyacencia no lo define.

Para grafos con algoritmos, tipos de arista, multigrafos, pesos o recorridos avanzados, JGraphT es una biblioteca de terceros mantenida por su proyecto y publicada en Maven Central. Su sitio oficial identifica `org.jgrapht:jgrapht-core:1.5.3` como versión estable publicada al corte y ofrece documentación y ejemplos [71]. No pertenece a Java SE ni al JDK; se debe declarar como dependencia y comprobar sus requisitos/licencia antes de incorporarla.

```xml
<dependency>
  <groupId>org.jgrapht</groupId>
  <artifactId>jgrapht-core</artifactId>
  <version>1.5.3</version>
</dependency>
```

#### Complejidad y selección

Big O describe cómo crece el trabajo cuando crece la cantidad de datos; no predice segundos absolutos. Las complejidades de esta tabla siguen los contratos y notas de implementación documentados para las clases Java SE citadas. En particular, “esperado” para estructuras hash depende de la distribución de `hashCode`, y no equivale a una garantía de tiempo constante para cualquier entrada. La latencia medida también depende de la JVM, el proveedor del JDK, versión, recolector, sistema operativo, hardware, carga, tamaño de datos y calentamiento del compilador JIT. No extrapoles una estimación Big O a un benchmark [52] [54] [53] [66] [51] [70].

| Necesidad dominante | Elección habitual | Costes orientativos | Consideraciones |
|---|---|---|---|
| Tamaño fijo, índices y datos primitivos | `int[]`, `double[]`, etc. | Índice O(1); buscar O(n); inserción con desplazamiento O(n). | Longitud fija; sin boxing de primitivos. |
| Secuencia mutable de propósito general | `ArrayList<E>` | `get`/`set` O(1); `add` al final O(1) amortizado; búsqueda/inserción interior O(n). | Opción por defecto para listas si no hay razón para otra. |
| Lista con operaciones de ambos extremos | `LinkedList<E>` | Acceso indexado O(n); trabajo de localizar posición O(n). | Implementa también `Deque`; mayor coste de referencias/nodos y menos apropiada para acceso aleatorio. |
| Unicidad y pertenencia rápida sin orden | `HashSet<E>` | `add`/`contains`/`remove` O(1) esperado si el hash distribuye bien. | Iteración O(capacidad + tamaño); sin orden garantizado. |
| Unicidad con orden | `TreeSet<E>` | Operaciones básicas O(log n). | Orden natural o comparador; criterio de comparación coherente con `equals`. |
| Búsqueda clave-valor general | `HashMap<K,V>` | `get`/`put` O(1) esperado con buen hash. | Sin orden garantizado; la iteración considera capacidad y tamaño. |
| Mapa con claves ordenadas/rangos | `TreeMap<K,V>` | `get`/`put`/`remove` O(log n). | Admite navegación y vistas de rangos ordenados. |
| LIFO o FIFO en memoria local | `ArrayDeque<E>` | La mayoría de operaciones de extremos O(1) amortizado. | No admite `null`; no es thread-safe. |
| Recuperar repetidamente el menor/mayor por prioridad | `PriorityQueue<E>` | Insertar/extraer O(log n); consultar extremo O(1). | No es FIFO; iterar no devuelve orden prioritario. |
| Grafo con algoritmos de biblioteca | JGraphT u otra biblioteca evaluada | Depende de representación y algoritmo. | Tercero: agrega dependencia, licencia y versión al mantenimiento. |

Criterios prácticos:

1. Elige primero la semántica: ¿se permiten duplicados?, ¿el orden importa?, ¿se necesita clave-valor?, ¿se necesita recuperar por índice, extremos o prioridad?
2. Después identifica las operaciones frecuentes y sus tamaños. Si predominan indexación y recorrido, empieza con `ArrayList`; si predomina pertenencia, valora `HashSet`; si se requiere orden natural, `TreeSet` o `TreeMap`.
3. Para LIFO/FIFO, usa la interfaz `Deque` y una clase apropiada, normalmente `ArrayDeque`. No uses `PriorityQueue` como cola FIFO ni confundas el orden de su iterador con la prioridad.
4. Considera nullabilidad, mutabilidad, capacidad, seguridad entre hilos y semántica de claves/orden. Estos contratos no son iguales en todas las clases.
5. Mide con datos representativos antes de optimizar. La localidad de memoria y constantes de implementación pueden hacer que una estructura asintóticamente atractiva sea más lenta para el tamaño real del problema.

Desde Java 21, `SequencedCollection`, `SequencedSet` y `SequencedMap` expresan colecciones con orden de encuentro y añaden operaciones uniformes de extremos y vistas invertidas como `reversed()`. JEP 431 registra esta característica como entregada en Java 21. No convierte `HashSet` ni `HashMap` en colecciones ordenadas: solo las implementaciones que ofrecen el contrato secuenciado lo cumplen [72].

```java
LinkedHashSet<String> pasos = new LinkedHashSet<>(List.of("inicio", "medio", "fin"));
System.out.println(pasos.getFirst());
System.out.println(pasos.reversed());
```

Salida esperada en Java 21 o posterior:

```text
inicio
[fin, medio, inicio]
```

#### Ejemplo integral ejecutable

Este archivo reúne operaciones de array, `List`, `Set`, `Map`, `TreeMap`, pila, cola, cola de prioridad, el contrato `equals`/`hashCode` y una búsqueda BFS. Sus identificadores y mensajes están en inglés donde pertenecen a la sintaxis de Java; la explicación y las conclusiones son en español.

```java
import java.util.ArrayDeque;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Deque;
import java.util.HashMap;
import java.util.HashSet;
import java.util.LinkedHashMap;
import java.util.LinkedHashSet;
import java.util.List;
import java.util.Map;
import java.util.Objects;
import java.util.PriorityQueue;
import java.util.Set;
import java.util.TreeMap;

public class EstructurasDemo {
    public static void main(String[] args) {
        int[] notas = {8, 10, 7};
        Arrays.sort(notas);
        System.out.println("array=" + Arrays.toString(notas));

        List<String> tareas = new ArrayList<>(List.of("leer", "probar"));
        tareas.add("entregar");
        tareas.set(0, "repasar");
        System.out.println("list=" + tareas + ", first=" + tareas.get(0));

        Set<String> etiquetas = new HashSet<>();
        etiquetas.add("java");
        etiquetas.add("java");
        System.out.println("set size=" + etiquetas.size()
                + ", contains=" + etiquetas.contains("java"));

        Map<String, Integer> visitas = new HashMap<>();
        visitas.merge("/inicio", 1, Integer::sum);
        visitas.merge("/inicio", 1, Integer::sum);
        System.out.println("map /inicio=" + visitas.get("/inicio"));
        TreeMap<String, Integer> ordenadas =
                new TreeMap<>(Map.of("b", 2, "a", 1));
        System.out.println("treemap first=" + ordenadas.firstKey());

        Deque<String> pila = new ArrayDeque<>();
        pila.push("primero");
        pila.push("encima");
        System.out.println("stack pop=" + pila.pop());
        Deque<String> cola = new ArrayDeque<>();
        cola.offerLast("A");
        cola.offerLast("B");
        System.out.println("queue poll=" + cola.pollFirst());

        PriorityQueue<Integer> prioridad = new PriorityQueue<>();
        prioridad.addAll(List.of(5, 1, 3));
        System.out.println("priority=" + prioridad.poll()
                + ", next=" + prioridad.peek());

        Map<Clave, String> porClave = new HashMap<>();
        porClave.put(new Clave("X7"), "encontrado");
        System.out.println("equals/hashCode=" + porClave.get(new Clave("X7")));

        Map<String, List<String>> grafo = new LinkedHashMap<>();
        grafo.put("A", List.of("B", "C"));
        grafo.put("B", List.of("D"));
        grafo.put("C", List.of("D"));
        grafo.put("D", List.of());
        System.out.println("BFS=" + bfs(grafo, "A"));

        LinkedHashSet<String> secuencia =
                new LinkedHashSet<>(List.of("uno", "dos", "tres"));
        System.out.println("reversed=" + secuencia.reversed());
    }

    static List<String> bfs(Map<String, List<String>> grafo, String inicio) {
        List<String> recorrido = new ArrayList<>();
        Set<String> vistos = new HashSet<>();
        Deque<String> pendientes = new ArrayDeque<>();
        vistos.add(inicio);
        pendientes.addLast(inicio);
        while (!pendientes.isEmpty()) {
            String actual = pendientes.removeFirst();
            recorrido.add(actual);
            for (String vecino : grafo.getOrDefault(actual, List.of())) {
                if (vistos.add(vecino)) pendientes.addLast(vecino);
            }
        }
        return recorrido;
    }

    private static final class Clave {
        private final String valor;

        private Clave(String valor) {
            this.valor = Objects.requireNonNull(valor);
        }

        @Override
        public boolean equals(Object objeto) {
            if (this == objeto) return true;
            if (!(objeto instanceof Clave otra)) return false;
            return valor.equals(otra.valor);
        }

        @Override
        public int hashCode() {
            return Objects.hash(valor);
        }
    }
}
```

Comandos para compilar y ejecutar:

```bash
javac EstructurasDemo.java
java EstructurasDemo
```

Salida comprobada con OpenJDK 21.0.13.1:

```text
array=[7, 8, 10]
list=[repasar, probar, entregar], first=repasar
set size=1, contains=true
map /inicio=2
treemap first=a
stack pop=encima
queue poll=A
priority=1, next=3
equals/hashCode=encontrado
BFS=[A, B, C, D]
reversed=[tres, dos, uno]
```

`HashSet` y `HashMap` se usan sin imprimir su orden, que no está garantizado. Se usa `TreeMap` para requerir primera clave ordenada y `LinkedHashMap`/listas ordenadas para que la salida BFS sea determinista. El ejemplo no incluye el JAR externo de JGraphT.

#### Errores frecuentes y correcciones

- **Confundir interfaz con clase:** `new List<>()` no es válido. Declara `List<String> xs = new ArrayList<>();` o la clase concreta que corresponda.
- **Usar el límite superior del array:** el último índice es `length - 1`; un bucle debe usar `i < array.length`, no `i <= array.length`.
- **Suponer que un array cambia de tamaño:** crea uno nuevo, por ejemplo con `Arrays.copyOf`, y copia o transforma los datos.
- **Usar primitivos como argumentos genéricos:** `List<int>` no compila; se usa `List<Integer>`. Para evitar boxing en datos numéricos intensivos, un array primitivo puede ser más apropiado.
- **Esperar que `List.of` sea mutable:** sus modificadores lanzan `UnsupportedOperationException`. Crea `new ArrayList<>(List.of(...))` si necesitas una copia modificable.
- **Tratar `Arrays.asList` como lista redimensionable:** admite reemplazo, no inserción/eliminación; está respaldada por el array original.
- **Hacer accesos indexados repetidos a `LinkedList`:** preferir un iterador o recorrido `for-each` cuando se procesa toda la lista; reservar `ArrayList` para acceso aleatorio frecuente.
- **Esperar orden de `HashSet` o `HashMap`:** si el orden es requisito, elige `TreeSet`/`TreeMap` para ordenar por comparación o una implementación `LinkedHash...` para orden de encuentro/inserción.
- **Sobrescribir `equals` y olvidar `hashCode`:** dos claves lógicamente iguales deben generar el mismo hash.
- **Mutar una clave almacenada en `HashMap`:** si cambian los campos usados para `equals`/`hashCode`, la búsqueda puede dejar de encontrar la entrada; usa claves inmutables.
- **Confundir `remove` en una lista de enteros:** `lista.remove(1)` selecciona el índice 1; `lista.remove(Integer.valueOf(1))` busca el objeto con valor 1.
- **Esperar que el iterador de `PriorityQueue` esté ordenado:** extrae elementos con `poll` o ordena una copia.
- **Utilizar `Stack` como primera opción:** para una pila nueva, prefiere `Deque` con `ArrayDeque`.
- **Usar una colección no segura entre hilos como si lo fuera:** `ArrayList`, `HashMap`, `ArrayDeque`, `PriorityQueue` y clases similares no ofrecen sincronización implícita. Un iterador *fail-fast* es una detección de errores de mejor esfuerzo, no un mecanismo de exclusión mutua [52] [60] [53] [51] [70].

#### Recomendaciones profesionales

Programa contra interfaces (`List`, `Set`, `Map`, `Deque`) cuando el algoritmo no necesita una operación exclusiva de una implementación. Mantén los tipos concretos visibles donde la selección sea relevante y documenta el motivo si la elección no es obvia. Usa colecciones genéricas parametrizadas; evita tipos crudos y casts innecesarios.

Haz explícitos el orden y la mutabilidad en APIs públicas. Usa `List.of`, `Set.of` o `Map.of` para datos no modificables pequeños; usa una copia modificable cuando el llamador deba cambiarlos. “No modificable” no significa “inmutable profundamente”: objetos mutables dentro aún pueden cambiar. Evita exponer directamente colecciones internas modificables si eso rompe invariantes de la clase.

Define `equals` y `hashCode` en conjunto y a partir de los mismos componentes semánticos. Mantén estables las claves y los elementos de `Set` mientras permanezcan dentro de estructuras hash. Para `TreeMap`, `TreeSet` y `PriorityQueue`, proporciona comparadores coherentes, transitivos y compatibles con los tipos almacenados.

No elijas `LinkedList` por la regla simplista de que “insertar es O(1)”: localizar un índice o nodo puede costar O(n), y para numerosos casos `ArrayList` o `ArrayDeque` resultan más simples. No reimplementes un árbol balanceado o un grafo por rutina. Una implementación propia es razonable para aprender, para estructura especializada probada o para restricciones que las bibliotecas estándar/terceras no satisfacen; en otro caso, reutiliza una implementación madura.

Documenta la versión mínima que requiere el código. `List.of`, `Set.of` y `Map.of` están disponibles desde Java 9; las interfaces secuenciadas y `reversed()` desde Java 21. El JDK 27 también incluye `jdk.incubator.vector`, una API incubadora distinta de las colecciones ordinarias; no es necesaria para los ejemplos ni debe tratarse como API estable [62] [64] [53] [72] [73]. Las APIs incubadoras pueden cambiar o eliminarse; JEP 11 describe ese propósito [74].

---

## 6. Paradigmas de programación

Un **paradigma** es una manera de estructurar y razonar sobre un programa. Java es multiparadigma: un mismo sistema puede organizar parte de su lógica en pasos imperativos, encapsular reglas en objetos, expresar transformaciones con funciones y coordinar tareas concurrentes. Estas etiquetas se solapan; no son modos mutuamente excluyentes ni categorías impuestas por el compilador.

#### Programación imperativa y estructurada

La programación **imperativa** expresa una secuencia de instrucciones que transforma el estado del programa: asigna variables, evalúa condiciones, recorre datos y llama métodos. Es el estilo de base de Java. La programación **estructurada** organiza ese flujo mediante secuencia, selección (`if`, `switch`) y repetición (`for`, `while`), en vez de saltos arbitrarios. Java conserva `goto` como palabra reservada, pero no permite usarla como instrucción ejecutable; normalmente se resuelve el flujo con bloques, métodos, excepciones o, en casos limitados, `break`/`continue` con etiqueta.

Este ejemplo imperativo calcula un total con descuento del 10 % solo para precios de 100 o más. También muestra selección y repetición estructuradas:

```java
import java.util.List;

public class Imperativo {
    public static void main(String[] args) {
        List<Integer> precios = List.of(100, 200, 300, 50);
        int total = 0;

        for (int precio : precios) {
            if (precio >= 100) {
                total += precio * 90 / 100;
            }
        }
        System.out.println(total);
    }
}
```

Guárdalo como `Imperativo.java` y ejecuta `javac Imperativo.java && java Imperativo`. La salida esperada es `540`. La lista es la entrada; `for` visita cada importe, `if` decide cuáles incluir y `total` conserva el estado acumulado. El patrón sirve para lógica con pasos y condiciones explícitos. Si se anidan demasiados bucles o condicionales, extrae operaciones con nombres que comuniquen intención; evita mantener contadores o estado mutables innecesarios cuando una transformación simple sea más clara.

#### Programación procedural

La programación **procedural** es una forma de organizar programas imperativos alrededor de procedimientos —en Java, métodos— que agrupan una tarea y reciben datos mediante parámetros. En Java no existe una declaración de función global independiente de una clase: un método se declara dentro de una clase, interfaz, enum o record. Un método `void` realiza una acción sin devolver resultado; un método con tipo de retorno produce un valor. La diferencia entre “procedural” e “imperativo” es de organización y énfasis, no una frontera estricta del lenguaje.

```java
import java.util.List;

public class Procedural {
    static int calcularTotal(List<Integer> precios) {
        int total = 0;
        for (int precio : precios) {
            if (precio >= 100) {
                total += precio * 90 / 100;
            }
        }
        return total;
    }

    public static void main(String[] args) {
        System.out.println(calcularTotal(List.of(100, 200, 300, 50)));
    }
}
```

La salida esperada es `540`. Separar `calcularTotal` de `main` facilita reutilizarlo y probarlo sin consola. Los métodos estáticos son útiles para algoritmos que no dependen de estado de instancia, pero no reemplazan automáticamente el modelado con objetos cuando existen reglas y estado que pertenecen a una entidad. Evita métodos extensos que mezclen entrada/salida, reglas de negocio y almacenamiento persistente.

#### Programación orientada a objetos

La **programación orientada a objetos (POO)** modela conceptos mediante objetos que combinan estado y operaciones, con encapsulamiento, abstracción y despacho dinámico. Java ofrece clases, instancias, constructores, campos, métodos, interfaces, clases abstractas, herencia y composición. Una clase solo puede extender una clase, pero puede implementar varias interfaces; el polimorfismo permite invocar una operación mediante un tipo común y obtener la implementación correspondiente al objeto concreto. Los `record`, disponibles desde Java 16, son clases de datos con sintaxis reducida; no convierten Java en un lenguaje sin objetos [75].

La siguiente versión asigna la política de descuento a un pedido. La interfaz abstrae la regla y `Pedido` mantiene su propia lista inmutable y coordina el cálculo:

```java
import java.util.List;

interface PoliticaDescuento {
    int aplicar(int importe);
}

final class DescuentoDiezPorCiento implements PoliticaDescuento {
    @Override
    public int aplicar(int importe) {
        return importe * 90 / 100;
    }
}

final class Pedido {
    private final List<Integer> precios;
    private final PoliticaDescuento politica;

    Pedido(List<Integer> precios, PoliticaDescuento politica) {
        this.precios = List.copyOf(precios);
        this.politica = politica;
    }

    int total() {
        int suma = 0;
        for (int precio : precios) {
            if (precio >= 100) {
                suma += politica.aplicar(precio);
            }
        }
        return suma;
    }
}

public class EjemploOop {
    public static void main(String[] args) {
        var pedido = new Pedido(
                List.of(100, 200, 300, 50),
                new DescuentoDiezPorCiento());
        System.out.println(pedido.total());
    }
}
```

La salida esperada es `540`. `Pedido` protege su representación con campos privados y copia la lista recibida; `PoliticaDescuento` desacopla el pedido de una regla concreta. En un sistema real, el importe monetario normalmente debe representarse con `BigDecimal` o unidades menores enteras y reglas explícitas de redondeo: `int` aquí solo hace el ejemplo comparable y sencillo. Un error frecuente es crear clases solo para envolver datos o diseñar jerarquías profundas donde la composición sería más simple. Prefiere responsabilidades cohesionadas, contratos pequeños y polimorfismo cuando varias implementaciones realmente deban sustituirse.

#### Programación funcional: interfaces funcionales, lambdas y streams

Java incorporó expresiones lambda, referencias a métodos y operaciones masivas de colecciones en **Java 8**. Una lambda no tiene un tipo de función independiente: el compilador necesita inferir su tipo destino a partir de una **interfaz funcional**, que tiene un solo método abstracto relevante. La anotación `@FunctionalInterface` documenta esa intención y permite que el compilador detecte cambios incompatibles, pero no es obligatoria. Los métodos `default` y `static` de una interfaz no cuentan como métodos abstractos adicionales [20] [76] [77].

Las interfaces habituales de `java.util.function` incluyen `Predicate<T>` para una prueba que devuelve `boolean`, `Function<T,R>` para transformar un dato, `Consumer<T>` para consumirlo sin resultado y `Supplier<T>` para producir un valor sin argumentos. `UnaryOperator<T>` especializa una función cuyo tipo de entrada y salida coinciden. Java ofrece variantes primitivas como `IntPredicate` e `IntUnaryOperator` para evitar parte del encajonado (`boxing`) y desempaquetado. Las excepciones comprobadas no encajan directamente en las interfaces estándar de función; si una operación puede lanzarlas, diseña un contrato propio o trata el error explícitamente [77].

```java
import java.util.function.Function;
import java.util.function.Predicate;

public class Lambdas {
    public static void main(String[] args) {
        Predicate<Integer> esElegible = precio -> precio >= 100;
        Function<Integer, Integer> descontar = precio -> precio * 90 / 100;
        System.out.println(esElegible.test(200));
        System.out.println(descontar.apply(200));
        Function<String, String> limpiar = String::trim;
        System.out.println(limpiar.apply(" java "));
    }
}
```

La salida esperada es `true`, `180` y `java`, cada valor en una línea. La forma `precio -> ...` define una expresión lambda; la forma `String::trim` es una referencia a método. Una lambda puede capturar variables locales del bloque que la contiene solo si son `final` o efectivamente finales, es decir, si no se reasignan después de su inicialización. No es una garantía de que los objetos referenciados sean inmutables: una referencia local puede ser final aunque el objeto al que apunta siga siendo mutable [27].

Los **streams**, también disponibles desde Java 8, describen una tubería de operaciones agregadas sobre datos. `filter`, `map` y `sorted` son operaciones intermedias; son perezosas y no procesan la fuente hasta que se llama a una operación terminal, como `sum`, `collect`, `count` o `forEach`. Un stream se consume al terminar; para volver a procesar los datos se crea otro stream desde la fuente. `IntStream`, `LongStream` y `DoubleStream` evitan el encajonado en cálculos numéricos. Un stream no es una colección ni necesariamente una secuencia asíncrona [78].

```java
import java.util.List;

public class Streams {
    public static void main(String[] args) {
        List<Integer> precios = List.of(100, 200, 300, 50);
        int total = precios.stream()
                .filter(precio -> precio >= 100)
                .mapToInt(precio -> precio * 90 / 100)
                .sum();
        System.out.println(total);
    }
}
```

La salida esperada es `540`. `stream()` crea un flujo secuencial; `filter` conserva solo los importes elegibles; `mapToInt` calcula el descuento; `sum` termina la tubería y agrega los valores. Esta combinación puede ser más declarativa que el bucle, pero sigue ejecutándose dentro de Java y no es programación funcional pura: el lenguaje permite mutación, excepciones y efectos laterales. Separa las transformaciones puras de operaciones como escribir archivos o actualizar una base de datos.

Las tuberías paralelas se solicitan, por ejemplo, con `precios.parallelStream()`. El API permite procesamiento paralelo, pero no promete que resulte más rápido: importa el tamaño y particionabilidad de los datos, el coste por elemento, la cantidad de procesadores, el orden requerido y las operaciones intermedias. No modifiques colecciones compartidas desde lambdas de `map` o `filter`; los efectos laterales pueden producir carreras, resultados no deterministas o trabajo omitido por optimizaciones. Usa reducciones y colectores apropiados, y mide antes de adoptar paralelismo [78] [79].

**Ejemplo comparativo completo.** Este programa calcula el mismo total mediante un bucle imperativo, un método procedural, objetos, interfaces funcionales y una tubería declarativa con stream. Guárdalo como `ParadigmasJava.java`:

```java
import java.util.List;
import java.util.function.Function;
import java.util.function.Predicate;

interface PoliticaDescuento {
    int aplicar(int importe);
}

final class DescuentoDiezPorCiento implements PoliticaDescuento {
    @Override
    public int aplicar(int importe) {
        return importe * 90 / 100;
    }
}

final class Pedido {
    private final List<Integer> precios;
    private final PoliticaDescuento politica;

    Pedido(List<Integer> precios, PoliticaDescuento politica) {
        this.precios = List.copyOf(precios);
        this.politica = politica;
    }

    int total() {
        int suma = 0;
        for (int precio : precios) {
            if (precio >= 100) suma += politica.aplicar(precio);
        }
        return suma;
    }
}

public class ParadigmasJava {
    static int totalProcedural(List<Integer> precios) {
        int suma = 0;
        for (int precio : precios) {
            if (precio >= 100) suma += precio * 90 / 100;
        }
        return suma;
    }

    public static void main(String[] args) {
        List<Integer> precios = List.of(100, 200, 300, 50);

        int imperativo = 0;
        for (int precio : precios) {
            if (precio >= 100) imperativo += precio * 90 / 100;
        }
        System.out.println("imperativo=" + imperativo);
        System.out.println("procedural=" + totalProcedural(precios));
        System.out.println("oop=" + new Pedido(
                precios, new DescuentoDiezPorCiento()).total());

        Predicate<Integer> elegible = precio -> precio >= 100;
        Function<Integer, Integer> descuento = precio -> precio * 90 / 100;
        int funcional = precios.stream()
                .filter(elegible)
                .map(descuento)
                .mapToInt(Integer::intValue)
                .sum();
        System.out.println("funcional=" + funcional);

        int declarativo = precios.stream()
                .filter(precio -> precio >= 100)
                .mapToInt(precio -> precio * 90 / 100)
                .sum();
        System.out.println("declarativo=" + declarativo);
    }
}
```

Compila y ejecuta con `javac ParadigmasJava.java && java ParadigmasJava` (JDK 10 o posterior, por `List.copyOf`). Salida verificada con OpenJDK 21.0.13.1:

```text
imperativo=540
procedural=540
oop=540
funcional=540
declarativo=540
```

El ejemplo no pretende que un estilo sea siempre superior: el bucle expone cada paso; el método procedural extrae una tarea; la versión orientada a objetos agrupa política y estado; las formas funcional y declarativa enfatizan las transformaciones. La etiqueta “declarativo” es relativa: la tubería describe qué filtrar, transformar y agregar, aunque el programador aún selecciona explícitamente operaciones Java.

#### Programación declarativa

La programación **declarativa** expresa principalmente qué resultado o transformación se desea, dejando más detalles de iteración y ejecución a una abstracción. Los streams de Java permiten escribir operaciones de alto nivel y una consulta puede leerse como una receta de transformaciones; por ello se habla de estilo declarativo o funcional-declarativo. Java, sin embargo, no es un lenguaje declarativo puro: el flujo de control y la mutación siguen disponibles, y la tubería de stream no equivale a una consulta SQL ni a un motor relacional que pueda reordenar libremente operaciones con semánticas distintas. Evita afirmar que `stream()` automáticamente optimiza o paraleliza: por defecto el stream es secuencial [78].

Este estilo resulta útil para filtrar, convertir, agrupar y resumir colecciones con una tubería corta y sin estado externo. Cuando las operaciones requieren muchas ramas, manejo contextual de errores o efectos laterales, un bucle nombrado y probado puede ser más claro que encadenar operadores.

#### Programación reactiva mediante bibliotecas

La programación **reactiva** organiza el procesamiento como una cadena de eventos o datos que llegan a lo largo del tiempo. Se usa en sistemas con flujos continuos, I/O asíncrona y numerosos clientes. Java incluye desde **Java 9** las interfaces `java.util.concurrent.Flow.Publisher`, `Subscriber`, `Subscription` y `Processor`, que corresponden semánticamente a las interfaces Reactive Streams. `Flow` aporta el protocolo de suscripción y demanda; no proporciona por sí solo un ecosistema completo de operadores, planificadores ni un framework de aplicación [80] [81].

Un framework de terceros como **Project Reactor** agrega tipos y operadores: `Flux<T>` representa de cero a muchos elementos y `Mono<T>` de cero o uno. Spring WebFlux es otro componente de terceros que ofrece un stack web reactivo basado en Reactive Streams. Estas tecnologías no forman parte de Java SE; las versiones, compatibilidad de JDK y actualizaciones dependen de cada proyecto. El ejemplo siguiente usa Reactor Core **3.8.8**, documentado como la versión estable vigente de su guía consultada al corte; el artefacto se distribuye por Maven Central [82] [83] [84].

Dependencia Maven para `pom.xml`:

```xml
<dependency>
  <groupId>io.projectreactor</groupId>
  <artifactId>reactor-core</artifactId>
  <version>3.8.8</version>
</dependency>
```

En un proyecto Maven que tenga configurados el compilador y el **Exec Maven Plugin**, ejecuta `mvn -q compile exec:java -Dexec.mainClass=ReactiveEjemplo`. La versión de Java configurada debe ser compatible con la versión elegida de Reactor; consulta sus notas de versión al fijar el JDK.

Programa `src/main/java/ReactiveEjemplo.java`:

```java
import reactor.core.publisher.Flux;

public class ReactiveEjemplo {
    public static void main(String[] args) {
        Flux.range(1, 10)
                .filter(n -> n % 2 == 0)
                .map(n -> n * n)
                .reduce(0, Integer::sum)
                .subscribe(
                        total -> System.out.println("suma=" + total),
                        error -> System.err.println("falló: " + error.getMessage()));
    }
}
```

La salida esperada según la lógica del ejemplo es `suma=220`: los cuadrados de 2, 4, 6, 8 y 10 se suman. No se verificó mediante ejecución en esta tarea; no se instaló ni descargó la dependencia Reactor. En Reactor una cadena describe el procesamiento y, normalmente, no comienza hasta la suscripción; una fuente como `Flux.range` puede emitir síncronamente. La programación reactiva no implica que cada operador cambie de hilo. El backpressure permite que el consumidor solicite elementos y module la demanda, pero este ejemplo usa la sobrecarga simple de `subscribe` y no demuestra control manual de demanda. `block()` puede servir para pruebas o programas de consola, pero bloquear hilos de un servidor reactivo suele frustrar el propósito del modelo [81] [82] [83] [84].

#### Concurrencia y paralelismo

La **concurrencia** permite que varias tareas progresen en intervalos solapados; el **paralelismo** es que ejecuten simultáneamente, por ejemplo en varios núcleos. Es posible tener concurrencia en un solo núcleo por intercalado de tareas sin simultaneidad. En Java, hilos (`Thread`), ejecutores (`ExecutorService`), futuros (`Future`, `CompletableFuture`), sincronizadores y streams paralelos ofrecen mecanismos distintos. La concurrencia puede combinarse con estilos imperativo, orientado a objetos, funcional o reactivo; no es un paradigma de organización del código en el mismo sentido que POO [85].

Los **hilos de plataforma** están asociados a hilos del sistema operativo. Los **hilos virtuales**, finalizados y estables desde **Java 21** (JEP 444), son hilos ligeros gestionados por la JVM y adecuados sobre todo para muchas tareas concurrentes que esperan I/O. No son una solución automática para cálculo intensivo de CPU, no hacen más rápido el trabajo por sí solos y no deben confundirse con un pool de hilos de plataforma. El uso y rendimiento dependen de JDK/JVM, las bibliotecas llamadas y el sistema operativo; las operaciones nativas o ciertos bloqueos pueden impedir que el hilo virtual se desmonte temporalmente de su hilo portador [86].

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class ConcurrenciaJava {
    public static void main(String[] args) throws Exception {
        try (ExecutorService executor =
                     Executors.newVirtualThreadPerTaskExecutor()) {
            Future<Integer> primera = executor.submit(() -> calcular(10));
            Future<Integer> segunda = executor.submit(() -> calcular(20));
            System.out.println(primera.get() + ", " + segunda.get());
        }
    }

    static int calcular(int valor) throws InterruptedException {
        Thread.sleep(50); // Simula una espera bloqueante breve.
        return valor * 2;
    }
}
```

Guárdalo como `ConcurrenciaJava.java`; compila con `javac ConcurrenciaJava.java` y ejecuta con `java ConcurrenciaJava` usando JDK 21 o posterior. Salida verificada en OpenJDK 21.0.13.1: `20, 40`. Las tareas pueden progresar concurrentemente mientras esperan; `Future.get()` obtiene sus resultados y el bloque `try` cierra el ejecutor. La salida se mantiene en ese orden porque se consulta primero `primera`, no porque las tareas terminen en ese orden. En código real, propaga interrupciones de forma consciente, define límites de tiempo, y limita explícitamente el acceso a recursos externos (por ejemplo, con un semáforo) si el servicio remoto no admite solicitudes ilimitadas.

La concurrencia introduce riesgos de visibilidad y carreras cuando varios hilos leen y modifican estado compartido. `synchronized`, `Lock`, tipos atómicos y estructuras concurrentes sirven para coordinar acceso, pero la primera opción suele ser compartir menos estado. No supongas que porque un entero o una colección “parece simple” las operaciones compuestas sean atómicas. Para trabajo de CPU independiente, mide `ForkJoinPool` o streams paralelos; para I/O bloqueante de gran concurrencia, evalúa hilos virtuales; para flujos asíncronos composables, valora Reactor u otro framework reactivo.

En **JDK 27**, la concurrencia estructurada (Structured Concurrency, JEP 533) continúa como **séptimo preview**: es una API preview, desactivada por defecto, no una característica estable. Puede cambiar o desaparecer entre versiones y exige habilitar preview al compilar y ejecutar. No la uses como base de compatibilidad de producción sin aceptar ese riesgo [87].

#### Límites, errores frecuentes y recomendaciones

- **Confundir lambda con una función de tipo nativo.** En Java la lambda necesita una interfaz funcional destino. Si el compilador no puede inferir ese tipo, declara la interfaz o el tipo de variable explícitamente.
- **Capturar y mutar estado desde un stream.** Además de que las variables locales capturadas deben ser efectivamente finales, mutar objetos externos puede causar interferencia o carreras. Usa `map`, `filter`, `reduce` y `collect` con acumuladores adecuados.
- **Suponer que una tubería se ejecutó.** Las operaciones intermedias son perezosas; sin operación terminal, normalmente no hay recorrido. No reutilices un stream después de una terminal.
- **Suponer que `parallelStream()` acelera cualquier cálculo.** El coste de dividir y combinar, el orden y las operaciones con estado pueden empeorar el tiempo o el uso de memoria. Mide con datos representativos.
- **Llamar reactivo a cualquier uso de `Flow` o `CompletableFuture`.** La mera asincronía no resuelve automáticamente contrapresión, cancelación, errores ni límites de recursos. Usa el protocolo y las garantías que proporcione la biblioteca concreta.
- **Bloquear una cadena reactiva o un hilo virtual sin considerar su contexto.** `block()` dentro de un servidor reactivo puede bloquear el event loop; operaciones bloqueantes prolongadas en hilos virtuales pueden retener recursos portadores según JDK, biblioteca y operación.
- **Diseñar toda solución como una jerarquía de clases.** Java permite métodos estáticos y funciones lambda, y no exige envolver cada dato en un objeto con comportamiento. Escoge abstracciones proporcionales al problema.
- **Confundir concurrencia con paralelismo.** Una tarea concurrente puede esperar o intercalarse sin ejecutarse al mismo tiempo que otra. Evalúa el tipo de carga antes de elegir hilos, ejecutores, streams paralelos o framework reactivo.

En código profesional, escoge el paradigma que haga visible la intención y facilite pruebas. Usa imperativo para pasos con estado y flujo complejo; métodos pequeños para separar tareas; objetos e interfaces para contratos y responsabilidades; lambdas y streams para transformaciones acotadas y sin efectos laterales; frameworks reactivos cuando el ciclo de vida de flujos asíncronos y la contrapresión sean requisitos reales; y abstracciones de concurrencia según el perfil I/O o CPU. Ningún paradigma elimina la necesidad de validar entradas, controlar errores, probar límites y medir rendimiento.

## 7. Modularidad y organización del código

### 7.1. Ideas esenciales: paquetes, módulos y bibliotecas

Un **paquete** (*package*) es un espacio de nombres que agrupa tipos relacionados y proporciona un nivel de acceso compartido. Su nombre cualificado, como `com.ejemplo.inventario.modelo`, evita colisiones entre tipos de proyectos distintos y expresa una zona del dominio. En el sistema de archivos habitual, cada segmento se refleja en un directorio: `com/ejemplo/inventario/modelo`. Los paquetes `com.ejemplo` y `com.ejemplo.inventario` son paquetes distintos; los subpaquetes no heredan acceso ni visibilidad del paquete padre [88].

Un **módulo** (*module*, JPMS) agrupa paquetes y declara qué otros módulos necesita y qué paquetes ofrece como API. Se describe mediante `module-info.java`, compilado como `module-info.class`. Un **JAR** (*Java Archive*) es un archivo ZIP que agrupa clases, recursos y metadatos. Un JAR puede no ser modular, o puede incluir el descriptor de un módulo. Un **artefacto** es una unidad distribuible identificada —por ejemplo— por coordenadas Maven `groupId:artifactId:version`; no es sinónimo de paquete Java, módulo ni JAR, aunque a menudo un artefacto se distribuya como JAR [89] [90].

Estas capas resuelven problemas diferentes. Los paquetes ordenan nombres y permiten colaboración de acceso dentro de ellos. Los módulos crean límites explícitos entre componentes y paquetes exportados. Los JAR empaquetan archivos. Maven y Gradle resuelven dependencias y automatizan compilación, pruebas y distribución. La declaración `import` solo permite escribir un nombre de tipo o miembro de forma abreviada dentro de un archivo fuente: **no** descarga bibliotecas ni declara una dependencia del módulo.

### 7.2. Declaración de paquetes e imports

En una unidad de compilación ordinaria, la declaración `package` aparece antes de los `import` y de las declaraciones de tipos. Si no hay `package`, el tipo pertenece al paquete sin nombre. Ese paquete resulta aceptable para ejercicios de un solo archivo, pero no es una organización recomendable para bibliotecas o aplicaciones con varios componentes; además, el código de un paquete con nombre no puede importar tipos del paquete sin nombre [88].

```java
package com.acme.inventario.modelo;

import java.math.BigDecimal;
import java.util.Objects;

public final class Producto {
    private final String codigo;
    private final BigDecimal precio;

    public Producto(String codigo, BigDecimal precio) {
        this.codigo = Objects.requireNonNull(codigo, "codigo");
        this.precio = Objects.requireNonNull(precio, "precio");
    }

    public String codigo() {
        return codigo;
    }

    public BigDecimal precio() {
        return precio;
    }
}
```

El nombre `com.acme.inventario.modelo.Producto` es el nombre cualificado del tipo. `import java.math.BigDecimal;` y `import java.util.Objects;` permiten referirse a esos tipos por su nombre simple. `java.lang` se importa implícitamente. También existen `import java.util.*;` e imports estáticos, como `import static java.util.Objects.requireNonNull;`; el comodín importa los tipos accesibles directamente en ese paquete, no sus subpaquetes. Los imports no alteran el alcance de acceso de un tipo [88].

Se puede omitir el import y emplear el nombre plenamente cualificado, por ejemplo `java.util.Objects.requireNonNull(codigo)`. Esto es útil cuando dos bibliotecas contienen tipos con igual nombre simple, aunque conviene reservarlo para evitar ambigüedad en puntos concretos. Un `import static` puede abreviar constantes o métodos estáticos, pero un exceso de ellos hace menos claro de dónde procede cada llamada.

**Errores habituales:** poner `package` después de un `import`; suponer que un import con `*` incorpora paquetes descendientes; creer que añadir un import incorpora un JAR a la compilación; o crear nombres de paquete basados solo en términos genéricos como `utils`. El orden y la correspondencia entre declaración y ruta son parte de una organización legible. Use nombres en minúsculas, evite palabras reservadas y, para proyectos distribuidos, prefiera un prefijo de dominio invertido bajo control de la organización, como `com.acme` [88] [91].

### 7.3. Clases top-level y disposición de archivos

Un **tipo top-level** es una clase, interfaz, enum, record o interfaz de anotación declarada directamente en una unidad de compilación, y no dentro de otro tipo. Java permite varias declaraciones top-level en un archivo fuente bajo las reglas de la especificación, pero los compiladores que usan archivos para localizar tipos pueden imponer la convención de que el tipo público corresponda al nombre del archivo. `javac` sigue esa convención: normalmente se escribe un tipo público principal por archivo (`Producto.java` declara `public class Producto`). Es posible añadir tipos auxiliares no públicos en ese archivo; para código mantenido, separarlos en archivos propios cuando tengan responsabilidades o uso independientes mejora la navegación [88].

En el nivel top-level solo se puede declarar el tipo como `public` o dejarlo sin modificador, lo que otorga acceso de paquete (*package-private*). `private` y `protected` no son válidos para un tipo top-level. Una clase miembro, en cambio, sí puede usar esos modificadores según las reglas para miembros. Java distingue mayúsculas y minúsculas, y el nombre de paquete debe concordar con la ruta por razones de interoperabilidad con compiladores y herramientas [88] [49].

```text
src/main/java/
└── com/acme/inventario/
    ├── api/
    │   └── Catalogo.java
    ├── modelo/
    │   └── Producto.java
    └── interno/
        └── ValidadorCodigo.java
```

Los directorios agrupan fuentes de acuerdo con su declaración `package`. No se deben colocar las clases de un mismo paquete en varios directorios con nombres distintos ni tratar un subpaquete como si fuera un espacio de acceso anidado. Un tipo auxiliar de implementación puede quedar package-private dentro de su paquete; no hay que hacer pública cada clase para que resulte accesible en toda la aplicación.

### 7.4. Modificadores de acceso y encapsulación

El control de acceso regula qué código puede nombrar una clase o utilizar un miembro. El **alcance** determina dónde un nombre está disponible en el texto; el **acceso** impone además las condiciones de visibilidad. Para campos, constructores y miembros de clase, los niveles básicos son [49]:

| Modificador | Código de la clase | Mismo paquete | Subclase en otro paquete | Cualquier código con acceso al tipo |
|---|---:|---:|---:|---:|
| `private` | Sí | No, salvo acceso desde la clase envolvente conforme a la especificación | No | No |
| *(sin modificador)* | Sí | Sí | No por ser subclase solamente | No |
| `protected` | Sí | Sí | Sí, con las restricciones de acceso de subclase | No |
| `public` | Sí | Sí | Sí | Sí, si el tipo y paquete son visibles |

En una interfaz, los miembros sin modificador tienen reglas particulares, por ejemplo, los métodos ordinarios de interfaz son públicos. `protected` no significa simplemente “visible a toda subclase en cualquier situación”: fuera del paquete se aplican restricciones que evitan acceder libremente al miembro protegido a través de cualquier instancia. En un tipo top-level, solo `public` o package-private son opciones.

La **encapsulación** consiste en mantener un estado y sus invariantes bajo control, exponiendo operaciones coherentes en lugar de permitir que cualquier llamador modifique los detalles internos. `private` ayuda a implementar esa frontera, pero no sustituye diseño: un campo público mutable no queda bien encapsulado por tener getters; un getter que devuelve directamente una colección interna mutable puede exponerla igualmente.

```java
package com.acme.inventario.modelo;

import java.util.ArrayList;
import java.util.List;
import java.util.Objects;

public final class Pedido {
    private final List<String> codigos = new ArrayList<>();

    public void agregar(String codigo) {
        codigos.add(Objects.requireNonNull(codigo, "codigo"));
    }

    public List<String> codigos() {
        return List.copyOf(codigos);
    }
}
```

`codigos` permanece privado. La mutación pasa por `agregar`, donde se valida el argumento, y el método de consulta devuelve una copia inmodificable (`List.copyOf`) en vez de entregar la lista mutable interna. La clase mantiene así un punto único donde proteger sus reglas. Esta API de colecciones pertenece al JDK; no es preview ni de terceros.

**Recomendaciones:** mantenga campos de instancia privados salvo que haya una razón concreta; prefiera inmutabilidad cuando sea viable; exponga el mínimo número de tipos y métodos; documente los contratos públicos; use package-private para colaboración estrictamente interna al paquete; y pruebe el comportamiento público. No convierta `protected` en un valor predeterminado para “facilitar tests”. Los tests que conocen todos los campos privados suelen quedar acoplados a la implementación y dificultar refactorizaciones.

### 7.5. JPMS y `module-info.java`

JPMS, el **Java Platform Module System**, se incorporó en Java 9. Un descriptor de módulo nombra el módulo, declara dependencias y define qué paquetes se exportan. Una declaración típica se ubica en la raíz de fuentes del módulo, junto a los directorios de paquetes, no dentro de un paquete [89] [21].

```java
// src/main/java/module-info.java
module com.acme.inventario {
    requires java.logging;

    exports com.acme.inventario.api;
}
```

Las directivas más comunes son:

- `requires nombre.modulo;` declara que el módulo necesita leer otro módulo. La dependencia debe resolverse al compilar o ejecutar.
- `exports paquete;` hace accesibles a otros módulos los tipos públicos del paquete, sujeto a sus propios modificadores de acceso. No exporta subpaquetes de manera recursiva.
- `exports paquete to moduloA, moduloB;` limita la exportación a módulos nombrados.
- `opens paquete;` permite acceso reflectivo profundo en ejecución al paquete, pero no es una exportación de API de compilación. `opens paquete to framework;` limita la apertura.
- `open module nombre.modulo { ... }` abre todos sus paquetes para reflexión; debe reservarse para casos que lo requieran.
- `requires transitive otro.modulo;` hace que los módulos que dependen del actual puedan leer también la dependencia indicada; úsese solo cuando un tipo de esa dependencia forma parte de la API expuesta.
- `requires static otro.modulo;` expresa una dependencia necesaria al compilar que puede ser opcional en ejecución.
- `uses servicio;` y `provides servicio with implementacion;` declaran consumidores y proveedores de servicios para `ServiceLoader` [89] [21].

Un ejemplo de módulo de aplicación puede usar un módulo de biblioteca sin publicar ningún paquete propio:

```java
module com.acme.inventario.app {
    requires com.acme.inventario;
}
```

`public` y `exports` responden a preguntas distintas. `public` habilita el acceso al tipo conforme a reglas del lenguaje; `exports` habilita a otro módulo a acceder al paquete. En un módulo nombrado, un tipo público dentro de un paquete no exportado no forma parte de una API accesible por otros módulos. Del mismo modo, `exports` no hace públicos los miembros privados ni tipos package-private. Los paquetes que no se exportan u abren permanecen encapsulados frente a otros módulos [89] [49].

JPMS no es un administrador de dependencias. La directiva `requires` no incluye coordenadas, URL ni versión: declara una relación de lectura entre nombres de módulos. Maven o Gradle siguen encargándose de localizar y seleccionar versiones de bibliotecas. Las directivas de módulo expresan arquitectura; la configuración del build resuelve artefactos concretos [89] [21].

**Errores frecuentes:** confundir `exports` con `opens`; olvidar exportar un paquete API; exportar todos los paquetes por comodidad; poner `module-info.java` dentro de `com/acme`; o suponer que el nombre del módulo se deriva automáticamente del nombre del paquete. Evite usar `--add-exports` y `--add-opens` como arreglo permanente: son opciones de lanzamiento/compilación para casos de compatibilidad o diagnóstico y no sustituyen un descriptor correcto [21] [92].

### 7.6. Classpath frente a module-path

El **classpath** (`-cp`, `--class-path`) busca clases y recursos individuales en directorios o archivos JAR. El **module-path** (`-p`, `--module-path`) busca definiciones completas de módulos y, con ellas, el grafo de dependencias declarado. El separador de rutas es `:` en la mayoría de sistemas POSIX y `;` en Windows; las herramientas también admiten directorios de módulos según la operación [21] [29].

| Aspecto | Classpath | Module-path |
|---|---|---|
| Unidad de búsqueda | Directorio/JAR con clases y recursos | Módulo modular, JMOD o directorio de módulo, según herramienta |
| Código sin `module-info` | Forma parte del módulo sin nombre (*unnamed module*) | Un JAR tradicional puede convertirse en módulo automático |
| Fronteras | Mayor compatibilidad histórica; todos los JAR del classpath quedan en el módulo sin nombre | Dependencias explícitas; los paquetes no exportados quedan encapsulados |
| Dependencias | Se agregan a la ruta y se resuelven al cargar | Se resuelve el grafo requerido; no selecciona versiones por sí solo |
| Sintaxis de arranque | `java -cp ... paquete.Clase` | `java --module-path ... --module modulo/paquete.Clase` |

El módulo sin nombre mantiene compatibilidad con aplicaciones antiguas: las clases del classpath se reúnen ahí, y ese módulo lee los módulos resueltos. Un JAR modular situado en el classpath se comporta como código no modular para ese lanzamiento. En sentido inverso, un JAR tradicional colocado en el module-path pasa a ser un **módulo automático**; su nombre puede venir de `Automatic-Module-Name` o inferirse del nombre del archivo. Los módulos automáticos son útiles como puente de migración, pero esa inferencia hace frágil cambiar arbitrariamente el nombre del JAR [21] [93].

Un ejemplo sin módulos, para código ubicado en `src/com/acme/Hola.java`, sería compilarlo a `out` y lanzarlo con `java -cp out com.acme.Hola`. Para proyectos nuevos pequeños puede ser suficiente. Al emplear librerías, la ruta debe incluir también sus JAR; un classpath incompleto produce errores de clase no encontrada. No use la variable global `CLASSPATH` como sustituto de una configuración por proyecto: puede contaminar compilaciones de distintas aplicaciones [29].

La ruta de módulos ofrece comprobaciones adicionales, pero no reemplaza pruebas de integración. Evite tener dos versiones del mismo módulo en rutas observables o dividir paquetes de forma accidental entre módulos nombrados. El sistema de módulos no es un gestor de versiones: no elige por usted la dependencia correcta si varias resuelven al mismo módulo [21].

### 7.7. JAR, manifiesto y punto de entrada

Un JAR agrupa `.class`, recursos y, opcionalmente, metadatos bajo `META-INF`. Un **JAR modular** contiene `module-info.class` en la raíz y puede colocarse en el module-path. Un JAR tradicional no contiene descriptor. El manifiesto `META-INF/MANIFEST.MF` puede incluir metadatos, entre ellos `Main-Class` para lanzar con `java -jar`. Crear un JAR no implica que las dependencias externas queden incluidas: muchos builds generan un JAR delgado que requiere gestionar por separado su classpath o module-path [90].

Para aplicaciones Java convencionales, el punto de entrada histórico es un método `public static void main(String[] args)`. La JVM recibe los argumentos como cadenas. El método debe delegar pronto en clases del dominio para que la lógica pueda probarse sin iniciar el proceso entero. Java 25 finalizó mediante JEP 512 las declaraciones `main` de instancia y los archivos de fuente compactos; esos formatos permiten programas pequeños sin clase explícita, pero no reemplazan la estructura convencional de paquetes y módulos de una aplicación profesional [30] [94].

```java
package com.acme.greet.cli;

import com.acme.greet.api.GreetingService;

public final class Main {
    private Main() {}

    public static void main(String[] args) {
        String name = args.length == 0 ? "Java" : args[0];
        System.out.println(new GreetingService().greet(name));
    }
}
```

En el modo clásico, el lanzador busca esa clase. Si no recibe un argumento, usa `Java`; así se evita acceder a `args[0]` cuando el arreglo está vacío. `GreetingService` es la lógica del ejemplo modular anterior y puede probarse aparte. En un producto real, el método `main` debe ser un adaptador delgado que delega el trabajo de dominio y las decisiones complejas.

Con un manifiesto que contiene, por ejemplo, `Main-Class: com.acme.greet.cli.Main`, el JAR ejecutable se lanza con:

```bash
java -jar build/greet.jar
```

Para un JAR modular, se puede usar el nombre de módulo y la clase principal:

```bash
java --module-path build/greet.jar \
  --module com.acme.greet/com.acme.greet.cli.Main
```

También puede registrarse la clase de inicio en el descriptor del JAR al crearlo con `jar --main-class`; en ese caso el lanzador modular puede omitir el nombre de clase y ejecutar el módulo. `java -jar` y `java --module-path ... --module ...` son modos distintos: no mezcle opciones pensando que `-jar` usará las rutas classpath configuradas aparte. `Main-Class` debe ser el nombre cualificado de una clase, sin sufijo `.class` [90] [95].

Con la estructura de fuentes `src/main/java/module-info.java`, `com/acme/greet/api/GreetingService.java` y `com/acme/greet/cli/Main.java` de este ejemplo, estos comandos POSIX compilan, ejecutan la clase modular, crean un JAR modular y vuelven a ejecutarlo desde el archivo:

```bash
mkdir -p build/mods/com.acme.greet
javac -d build/mods/com.acme.greet \
  $(find src/main/java -name '*.java' -print)
java --module-path build/mods \
  --module com.acme.greet/com.acme.greet.cli.Main Ada
jar --create --file build/greet.jar \
  --main-class com.acme.greet.cli.Main \
  -C build/mods/com.acme.greet .
java --module-path build/greet.jar --module com.acme.greet Ada
```

Salida de ambas invocaciones de Java:

```text
Hola, Ada!
Hola, Ada!
```

Estos comandos y ambas líneas de salida sí se comprobaron con OpenJDK 21.0.13.1; la sintaxis modular empleada está disponible desde Java 9. `find` y la continuación con `\` corresponden a una shell POSIX; en PowerShell o `cmd.exe` use la sintaxis de esos entornos y enumere los archivos fuente explícitamente o emplee una lista de argumentos para `javac` [95] [96].

### 7.8. Organización profesional y separación de responsabilidades

La organización debe permitir encontrar el código por su función y entender las dependencias sin leer toda la aplicación. Una estructura inicial habitual, válida para Maven y Gradle, es:

```text
inventario/
├── pom.xml                    # o build.gradle.kts; elija un build principal
├── README.md
├── LICENSE
├── .gitignore
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   ├── module-info.java
│   │   │   └── com/acme/inventario/
│   │   │       ├── api/Catalogo.java
│   │   │       ├── modelo/Producto.java
│   │   │       ├── interno/RepositorioMemoria.java
│   │   │       └── cli/Main.java
│   │   └── resources/          # configuración/plantillas empaquetadas
│   └── test/
│       ├── java/
│       │   └── com/acme/inventario/api/CatalogoTest.java
│       └── resources/          # datos exclusivos para pruebas
└── target/                     # Maven; generado, no se versiona
```

Maven define convencionalmente `src/main/java`, `src/main/resources`, `src/test/java` y `src/test/resources`, con resultados en `target`. Gradle adopta el mismo patrón de conjuntos de fuentes Java, normalmente con resultados bajo `build`. Los detalles generados deben excluirse de control de versiones. En una biblioteca compartida, `api` puede contener el contrato público y los paquetes de implementación pueden quedar sin exportar en `module-info.java`. Evite paquetes vagos como `common` si mezclan responsabilidades no relacionadas [97] [98].

A medida que crece el código, puede convenir separar componentes en varios módulos, o varios proyectos dentro de un build multiproyecto. No divida en módulos solo para aumentar el número de carpetas: el límite modular debe reflejar una frontera de API, dependencias o despliegue que aporte valor. En Maven, los subproyectos pueden coordinarse con un POM padre y módulos; en Gradle, con `settings.gradle(.kts)` y subproyectos. La sintaxis de configuración de ambos productos es propia de sus herramientas, no Java.

### 7.9. Build, dependencias y elección de herramienta

Un **build** automatiza pasos repetibles: validar configuración, procesar recursos, compilar código de producción, compilar y ejecutar pruebas, empaquetar y, si corresponde, publicar. El **gestor de dependencias** obtiene artefactos desde repositorios y coordina sus dependencias transitivas. Maven utiliza un `pom.xml` declarativo y un ciclo de vida con fases; Gradle usa un DSL Groovy o Kotlin, tareas y plugins. Se recomienda elegir una herramienta por proyecto y utilizar su wrapper (`mvnw` o `gradlew`) para fijar la versión del build que ejecuta el equipo, en vez de depender de una instalación global implícita [97] [99] [100].

Maven tiene fases como `validate`, `compile`, `test`, `package`, `verify`, `install` y `deploy`. Ejecutar una fase también ejecuta las fases anteriores del ciclo correspondiente. `mvn test` ejecuta pruebas unitarias configuradas; `mvn package` genera el artefacto; `mvn verify` llega a las verificaciones finales configuradas. `install` copia el artefacto al repositorio local para otros proyectos del equipo. `deploy` normalmente publica a un repositorio remoto y no debería ejecutarse sin la configuración y autorización correspondientes [99].

Ejemplo mínimo de `pom.xml` con Java 27 y JUnit Jupiter 6.1.3:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.acme</groupId>
  <artifactId>inventario</artifactId>
  <version>1.0.0</version>

  <properties>
    <maven.compiler.release>27</maven.compiler.release>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <junit.version>6.1.3</junit.version>
  </properties>

  <dependencies>
    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter</artifactId>
      <version>${junit.version}</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.16.0</version>
        <configuration>
          <release>${maven.compiler.release}</release>
        </configuration>
      </plugin>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>3.6.1</version>
      </plugin>
    </plugins>
  </build>
</project>
```

La opción `release` configura nivel de lenguaje, formato de bytecode y APIs públicas de Java disponibles para compilar; usar solo `source` y `target` no impide por sí mismo referenciar API nueva. No se puede compilar para una versión posterior a la del `javac` instalado. Así, `release=27` requiere un JDK 27 o posterior compatible; el build con `javac` 21 fallaría para esa selección. Si se desarrolla para despliegue Java 25, se debe cambiar a `25` y construir con JDK adecuado. Esta versión objetivo del compilador no garantiza que el entorno de producción tenga los mismos parches o configuración de runtime [101] [96].

La dependencia JUnit se declara con alcance `test`, por lo que no se convierte en dependencia de producción. JUnit 6 requiere Java 17 o superior para ejecutar sus pruebas; el JDK del equipo debe satisfacer tanto este requisito como el `release` configurado [102]. El artefacto `org.junit.jupiter:junit-jupiter:6.1.3` está publicado en Maven Central [103]. Los números de versión del ejemplo están fijados para que el build sea reproducible; deben actualizarse deliberadamente, revisando notas de publicación, compatibilidad, soporte y seguridad, no mediante rangos flotantes [102] [104] [105].

Gradle Kotlin DSL para una aplicación modular con el mismo punto de entrada:

```kotlin
plugins {
    application
}

repositories {
    mavenCentral()
}

java {
    toolchain {
        languageVersion.set(JavaLanguageVersion.of(27))
    }
}

dependencies {
    testImplementation("org.junit.jupiter:junit-jupiter:6.1.3")
}

tasks.test {
    useJUnitPlatform()
}

application {
    mainModule.set("com.acme.inventario")
    mainClass.set("com.acme.inventario.cli.Main")
}
```

El plugin `application` utiliza el plugin Java y permite ejecutar `run`, además de crear distribuciones con scripts de inicio para sistemas operativos compatibles. `mainModule` indica el módulo y `mainClass` el tipo de inicio. Si la aplicación no es modular, basta configurar `mainClass`. Gradle puede inferir el module-path al encontrar `module-info.java`, aunque el comportamiento y los requisitos de módulos de prueba dependen de la versión del plugin, el framework de tests y su configuración [98] [100].

**Maven, pasos usuales:**

```bash
./mvnw clean test
./mvnw package
./mvnw verify
```

**Gradle, pasos usuales:**

```bash
./gradlew clean test
./gradlew run --args="Ada"
./gradlew installDist
```

El wrapper de Windows se invoca normalmente como `mvnw.cmd` o `gradlew.bat`. La forma exacta de ejecutar depende del sistema operativo y de que el wrapper ya exista y tenga permisos. Como expectativa, `test` termina con `BUILD SUCCESS` o un resultado equivalente cuando todo pasa; el número de pruebas y el formato detallado dependen de plugins y configuración. Los comandos Maven/Gradle anteriores no se ejecutaron en el entorno de redacción, que no tenía esas herramientas instaladas.

### 7.10. Pruebas, empaquetado y verificación del ciclo

Las **pruebas unitarias** verifican una unidad pequeña, normalmente con colaboradores controlados. Las **pruebas de integración** verifican la colaboración real entre componentes o infraestructura. Las **pruebas funcionales** comprueban un requisito visible desde una interfaz o contrato de más alto nivel. Las categorías no vienen determinadas solo por el framework: dependen del alcance que la prueba verifica.

JUnit Jupiter ofrece anotaciones como `@Test` y aserciones; el motor JUnit, Maven Surefire o Gradle ejecutan y reportan las pruebas. JUnit es un framework de terceros. Un ejemplo de prueba de una API pública podría ser [102] [104] [100]:

```java
package com.acme.greet.api;

import static org.junit.jupiter.api.Assertions.assertEquals;

import org.junit.jupiter.api.Test;

class GreetingServiceTest {
    @Test
    void saludaPorNombre() {
        GreetingService servicio = new GreetingService();

        assertEquals("Hola, Ada!", servicio.greet("Ada"));
    }
}
```

La prueba verifica un resultado observable de `GreetingService`, clase definida antes en el ejemplo modular; no inspecciona campos privados. Para una prueba de integración, se podría conectar un repositorio real en un entorno controlado. No se debe usar una dependencia externa ni datos de producción por accidente. Un mock o stub puede aislar colaboraciones, pero simular en exceso las interacciones vuelve las pruebas frágiles y puede hacer que validen la configuración del mock en vez del comportamiento.

En módulos JPMS, el código de pruebas y el motor de pruebas pueden quedar en módulos o rutas distintas. Herramientas modernas ayudan a configurar el módulo de pruebas, pero el acceso reflectivo depende de `exports`, `opens`, paquetes y versión del framework. Si un error de pruebas menciona acceso reflectivo, revise la configuración modular del test y abra solo el paquete necesario al módulo del motor; no debilite todos los límites de producción de forma indiscriminada [89] [98] [100].

Una secuencia de ciclo profesional es: declarar el nivel de Java y dependencias; compilar; ejecutar pruebas; empaquetar; verificar que el JAR incluya descriptor, clases, recursos y manifiesto esperados; iniciar el artefacto como lo hará el usuario final; y probar al menos el JDK de producción. `jar --list --file target/inventario.jar` inspecciona el contenido; `jar --describe-module --file target/inventario.jar` informa el descriptor de un JAR modular. La estructura interna concreta del directorio de salida depende del build.

**Errores frecuentes de pruebas/build:** tests bajo `src/main/java`; dependencia JUnit con alcance de producción; tests que el plugin no descubre por nombre o configuración; distintas versiones de Java entre compilador, IDE, CI y producción; JAR considerado “ejecutable” sin clase principal; módulo principal no exportado o clase de inicio no accesible; confiar en una salida de IDE que el build limpio no reproduce; o no revisar las dependencias transitivas del artefacto.

### 7.11. Errores habituales y recomendaciones profesionales

1. **Todo es `public`.** Se pierde margen para cambiar implementación. Mantenga package-private y `private` hasta que exista una necesidad clara de API.
2. **Paquetes llamados `util`, `misc` o `common` que lo contienen todo.** Agrupe por dominio y responsabilidad; no confunda directorio con límite arquitectónico.
3. **Confundir paquete y módulo.** Una clase puede tener paquete `com.acme.app` y pertenecer a módulo `com.acme.application`; la correspondencia de prefijos es convención, no identidad.
4. **Suponer que `public` en un módulo equivale a público para todo el mundo.** El paquete debe estar exportado y los módulos deben leerlo.
5. **Confundir `exports` con `opens`.** El primero permite acceso a API pública en compilación/ejecución; el segundo habilita reflexión en ejecución. Abra solo lo que requiere un framework.
6. **Depender de módulos automáticos sin fijar sus nombres.** Declare `Automatic-Module-Name` si se publica una librería que aún no adopta `module-info.java`, o planifique una transición a módulo explícito.
7. **Agregar JARs manualmente en cada entorno.** Use un gestor de dependencias para fijar versiones, resolver transitivas y compartir la receta de build.
8. **Usar `source`/`target` en lugar de `release` como garantía de compatibilidad.** Para compilar contra API de versión inferior, use `--release` o la configuración equivalente del plugin [101] [96].
9. **Duplicar la misma biblioteca o clase en distintas rutas.** El classpath puede elegir una copia según el orden; el resultado puede ser diferente entre equipo, CI y producción.
10. **Hacer que `main` contenga todo el programa.** Manténgalo como adaptador de argumentos, composición inicial y salida; ubique reglas del dominio en componentes probables.
11. **Publicar un JAR sin probar cómo se lanza.** El comando exacto depende de si es JAR clásico, modular, thin o distribución completa.
12. **Abrir todos los paquetes o usar `--add-opens` permanentemente para que pasen los tests.** Analice el acceso requerido y documente la excepción más estrecha posible.

### 7.12. Resumen operativo

Para un ejercicio aislado, un archivo Java simple y `javac` pueden bastar. Para un proyecto real, cree paquetes con nombres estables, separe producción y tests, oculte la implementación y escriba una entrada delgada. Use Maven o Gradle para declarar herramientas y dependencias. Añada JPMS cuando los límites entre componentes, módulos publicables o control de reflexión aporten valor; el sistema de módulos está disponible desde Java 9, pero no es requisito para todo proyecto Java. Antes de distribuir, pruebe el artefacto y su comando de ejecución en el JDK y los sistemas previstos.

## 8. Memoria, objetos y gestión de recursos

#### Modelo de memoria de la JVM

La **Java Virtual Machine (JVM)** define áreas de datos lógicas que utiliza durante la ejecución. La especificación no obliga a una JVM a reproducirlas como segmentos físicos idénticos ni prescribe un recolector concreto. Por eso, las expresiones *stack* y *heap* son útiles para razonar sobre el modelo, pero no autorizan a inferir la dirección física de una variable o de un objeto [106].

La especificación distingue estas áreas principales [106]:

| Área definida por la JVM | Ámbito y función | Matiz importante |
|---|---|---|
| Registro `pc` | Uno por hilo Java; indica la instrucción de bytecode que ejecuta el hilo, salvo en métodos nativos, donde su valor no está definido. | Es un registro abstracto de la máquina virtual; no es una variable Java que manipule el programa. |
| Pila de la JVM (*Java Virtual Machine stack*) | Privada de cada hilo. Contiene marcos (*frames*) de las llamadas activas a métodos. Un marco mantiene variables locales abstractas, una pila de operandos y datos de ejecución. | Puede tener tamaño fijo o crecer dinámicamente según la implementación. La especificación permite que los marcos se asignen en el heap; no es preciso imaginar una pila física contigua. |
| Heap | Compartido por los hilos. Es el área de ejecución de la que se obtiene almacenamiento para instancias de clases y arrays; la JVM recupera automáticamente el almacenamiento de objetos. | La especificación no fija el algoritmo, los tiempos ni la política del GC. El heap no tiene que ser contiguo y puede crecer o reducirse según la implementación. |
| Área de métodos (*method area*) | Compartida. Contiene estructuras por clase, como datos de campos y métodos, código y referencias al *run-time constant pool*. | Es una categoría lógica de la JVMS; su ubicación y administración física dependen de la JVM. |
| *Run-time constant pool* | Uno por clase o interfaz; representa en ejecución la tabla de constantes del archivo `.class`, incluidas constantes y referencias simbólicas a campos o métodos. | La JVMS lo sitúa lógicamente en el área de métodos. |
| Pila de métodos nativos | Puede respaldar métodos `native` y código interno de la implementación. | Su existencia y configuración dependen de la JVM y del uso de código nativo. |

La descripción didáctica «las variables locales siempre viven en la pila y todos los objetos siempre ocupan el heap de manera visible» es demasiado rígida. La especificación describe ranuras de variables locales y pila de operandos por marco, pero permite a la implementación cambiar la representación cuando conserva el comportamiento observable. Una JVM puede, por ejemplo, compilar bytecode a código nativo y optimizar asignaciones. El análisis de escape (*escape analysis*) puede ayudar a decidir si un objeto escapa de un ámbito, pero Java no garantiza que un objeto no escapado se asigne en la pila ni que cualquier asignación concreta se elimine o se materialice de una forma específica [106].

En HotSpot, **Metaspace** es el nombre de un mecanismo de implementación para metadatos de clases alojados en memoria nativa. No es un área con ese nombre definida por la JVMS, ni debe usarse como sinónimo exacto del área de métodos. Otras JVM pueden administrar esos datos de otra manera. La guía de diagnóstico de HotSpot también documenta errores `OutOfMemoryError` asociados a agotamiento de Metaspace o de memoria nativa [107].

## 9. Entrada, salida y serialización

#### Modelo de entrada y salida: bytes y caracteres

La **entrada/salida** (*I/O*) conecta un programa con la terminal, archivos, red y otros dispositivos. Una distinción fundamental es entre **flujos de bytes** (`InputStream`, `OutputStream`), que trasladan valores binarios sin interpretarlos, y **flujos de caracteres** (`Reader`, `Writer`), que leen o escriben texto ya decodificado o pendiente de codificación. Un **charset** o juego de caracteres define cómo convertir bytes y texto; UTF-8 es una codificación de texto, no un tipo de dato Java. Para texto, convierta bytes a caracteres una sola vez, usando la codificación pactada. Para imágenes, audio, archivos comprimidos y otros datos binarios, conserve los bytes y no los pase por un `Reader` [108] [109].

`InputStream.read(byte[])` y las variantes de lectura no prometen llenar el arreglo solicitado en una sola llamada: pueden entregar menos datos, y devuelven `-1` al alcanzar el fin de flujo. Para copiar flujos, use un bucle que atienda ese contrato o `transferTo` cuando convenga. `BufferedReader` y `BufferedInputStream` agregan memoria intermedia y reducen lecturas pequeñas repetidas; no cambian el significado del contenido. Evite envolver varias veces el mismo flujo o leerlo directamente después de haberlo entregado a un búfer, porque cada capa puede adelantar datos [109] [110].

#### Leer desde consola: `Console`, `Scanner` y `BufferedReader`

**`Console`.** `System.console()` devuelve el objeto `Console` de la JVM cuando hay una consola disponible. Puede devolver `null` en un IDE, una tarea automatizada, un proceso con entrada o salida redirigida, o un entorno sin terminal. Por ello, no asuma que una aplicación siempre tendrá consola interactiva. `Console.readLine` lee una línea; `readPassword` solicita texto sin eco y devuelve un `char[]`, que conviene borrar tras su uso. Los juegos de caracteres de la consola se relacionan con la entrada/salida de terminal y pueden diferir del charset predeterminado para archivos [111].

```java
import java.io.Console;
import java.util.Arrays;

public class EntradaConsola {
    public static void main(String[] args) {
        Console consola = System.console();
        if (consola == null) {
            System.err.println("No hay consola interactiva disponible.");
            return;
        }

        String nombre = consola.readLine("Nombre: ");
        char[] clave = consola.readPassword("Contraseña: ");
        if (clave == null) {
            System.err.println("No se recibió una contraseña.");
            return;
        }

        try {
            consola.printf("Hola, %s.%n", nombre);
            // Aquí se usaría la contraseña sin convertirla a String.
        } finally {
            Arrays.fill(clave, '\0');
        }
    }
}
```

El ejemplo no imprime ni convierte la clave a `String`, porque un `String` no se puede borrar de forma fiable una vez creado. `readPassword` reduce su exposición, pero borrar el arreglo no garantiza que todas las copias internas o temporales hayan desaparecido. Pruebe programas interactivos desde un terminal real y trate por separado el caso `System.console() == null` [111].

**`Scanner`.** `java.util.Scanner` divide texto en tokens según un delimitador que por defecto es espacio en blanco y permite convertir tokens a tipos primitivos con métodos como `nextInt`. Es sencillo para ejercicios y entradas pequeñas. Sus métodos `next...` pueden fallar si no existe el siguiente token o si no se puede convertir al tipo esperado; `hasNextInt` permite comprobarlo. Para validar una entrada línea por línea, lea la línea completa y conviértala explícitamente, de modo que se pueda informar del error y volver a solicitar el dato. Para leer una línea sin separar tokens, use `nextLine` [112].

```java
import java.nio.charset.StandardCharsets;
import java.util.NoSuchElementException;
import java.util.Scanner;

public class EntradaScanner {
    public static void main(String[] args) {
        try (Scanner entrada = new Scanner(System.in, StandardCharsets.UTF_8)) {
            System.out.print("Edad: ");
            if (!entrada.hasNextLine()) {
                System.err.println("Fin de la entrada.");
                return;
            }

            String linea = entrada.nextLine().trim();
            try {
                int edad = Integer.parseInt(linea);
                if (edad < 0) {
                    System.err.println("La edad no puede ser negativa.");
                    return;
                }
                System.out.println("Edad registrada: " + edad);
            } catch (NumberFormatException ex) {
                System.err.println("Escriba un número entero.");
            }
        } catch (NoSuchElementException ex) {
            System.err.println("La entrada ya no está disponible.");
        }
    }
}
```

Para probarlo desde un terminal, guarde el archivo como `EntradaScanner.java` y ejecute:

```text
javac EntradaScanner.java
java EntradaScanner
```

Con la entrada `34`, la salida prevista es `Edad registrada: 34`. Con `treinta`, el programa informa que se espera un entero. La declaración de charset hace explícito el contrato de entrada del ejemplo; en una terminal cuya codificación no sea UTF-8, ajuste la codificación al entorno o use `Console`, que conoce el charset de la terminal. En una aplicación más amplia no cierre un `Scanner` construido sobre `System.in` si otras partes del programa aún necesitan esa entrada: cerrarlo cierra también el flujo subyacente [111] [112].

Un error frecuente es combinar `nextInt()` y `nextLine()` esperando que el segundo recoja la siguiente línea: `nextInt()` consume el token numérico, pero deja pendiente el separador de línea; `nextLine()` puede devolver el resto vacío de esa línea. Soluciones: mantenga una estrategia de lectura por líneas y convierta con `Integer.parseInt`, o consuma deliberadamente el resto de la línea después de `nextInt`. Evite mezclar varios lectores sobre `System.in`, porque sus búferes pueden competir por los mismos bytes [112].

**`BufferedReader`.** `BufferedReader` envuelve un `Reader` y almacena temporalmente caracteres para hacer eficiente la lectura. `readLine()` devuelve la línea sin el separador de línea, o `null` al fin de flujo. Resulta útil para entrada línea por línea y archivos largos; a diferencia de `Scanner`, no convierte automáticamente a números ni interpreta tokens. Convierta y valide los valores explícitamente [110].

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.nio.charset.StandardCharsets;

public class EntradaConBufferedReader {
    public static void main(String[] args) throws IOException {
        BufferedReader lector = new BufferedReader(
                new InputStreamReader(System.in, StandardCharsets.UTF_8));
        System.out.print("Escriba una línea: ");
        String linea = lector.readLine();
        if (linea == null) {
            System.out.println("Fin de la entrada.");
        } else {
            System.out.println("Recibido: " + linea);
        }
        // No se cierra System.in aquí: el proceso puede compartirlo.
    }
}
```

La entrada UTF-8 es una decisión explícita del ejemplo, no una garantía de que toda terminal envíe UTF-8. Si la aplicación administra por completo la entrada, `try`-with-resources es apropiado; si solo toma prestado `System.in`, no lo cierre antes de que otros componentes lo usen [111] [113].

#### Salida estándar: `System.out` y `System.err`

`System.out` es el flujo estándar de salida y `System.err` el de errores y diagnósticos. Ambos son `PrintStream`: ofrecen `print`, `println`, `printf` y `format`. Los programas y shells pueden redirigirlos por separado, lo cual permite conservar los resultados normales mientras los mensajes de diagnóstico se envían a otro destino. `System.out` no es un sistema de *logging*: para aplicaciones mantenibles, use una biblioteca o la API `java.util.logging` cuando necesite niveles, configuración y destinos. `PrintStream` no propaga `IOException` desde los métodos de impresión; registra internamente el error, que puede consultarse con `checkError()` [114].

```java
import java.util.Locale;

public class SalidaConsola {
    public static void main(String[] args) {
        double total = 19.5;
        System.out.printf(Locale.ROOT, "Total: %.2f%n", total);
        System.err.println("Diagnóstico: cálculo completado.");
    }
}
```

La salida prevista contiene `Total: 19.50` y `Diagnóstico: cálculo completado.` en líneas separadas, aunque el orden visual de ambos flujos puede variar cuando se redirigen por separado. `Locale.ROOT` evita que el separador decimal cambie por la configuración regional; `%n` usa el separador de línea de la plataforma. No cierre `System.out` ni `System.err` desde una biblioteca o una función que no sea dueña de esos flujos [114].

El charset de `System.out` y `System.err` no debe suponerse siempre igual al charset por defecto para archivos. JEP 400 establece UTF-8 por defecto para las API estándar desde JDK 18, con la excepción de la E/S de consola; la configuración y los detalles de consola pueden depender del JDK, vendor y sistema operativo. En protocolos de archivo o red, seleccione un charset explícito; para la terminal, no fuerce uno sin confirmar el entorno [115].

#### Rutas y archivos con `Path` y `Files`

`Path` representa una ruta en un proveedor de sistema de archivos y `Files` ofrece operaciones para leer, escribir, copiar, mover, consultar y recorrer archivos. La API pertenece a `java.nio.file` (NIO.2, incorporada en Java 7). `Path.of(...)` está disponible desde Java 11. Una ruta relativa se resuelve respecto del directorio de trabajo del proceso, no necesariamente respecto de la carpeta que contiene el código fuente. Los separadores, permisos, enlaces simbólicos y algunas operaciones dependen del sistema operativo y del proveedor del sistema de archivos [116] [117].

`Files.readString` y `Files.writeString` son convenientes para archivos de texto que caben razonablemente en memoria; están disponibles desde Java 11 y, si no se pasa charset, usan UTF-8. Las variantes con `Charset` explicitan el formato esperado. Para documentos grandes, prefiera `Files.newBufferedReader` o `Files.newBufferedWriter` y recorra el contenido en vez de cargarlo entero. Al escribir, compruebe si la operación crea, reemplaza o agrega al archivo: `writeString` sin opciones crea el archivo o trunca el existente. Use `CREATE_NEW` si sobrescribir un archivo existente no es aceptable [116].

```java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.StandardOpenOption;

public class ArchivoTexto {
    public static void main(String[] args) throws IOException {
        Path carpeta = Path.of("datos");
        Files.createDirectories(carpeta);
        Path archivo = carpeta.resolve("saludo.txt");

        Files.writeString(archivo, "Hola, Java\n", StandardCharsets.UTF_8,
                StandardOpenOption.CREATE,
                StandardOpenOption.TRUNCATE_EXISTING,
                StandardOpenOption.WRITE);

        String contenido = Files.readString(archivo, StandardCharsets.UTF_8);
        System.out.print(contenido);
    }
}
```

Comandos para compilar y ejecutar desde la carpeta que contiene el archivo:

```text
javac ArchivoTexto.java
java ArchivoTexto
```

La salida prevista es `Hola, Java`. El archivo creado queda en `datos/saludo.txt` bajo el directorio de trabajo actual. El programa declara UTF-8 tanto al escribir como al leer; la ruta y el contenido son asuntos distintos: el charset del contenido no determina cómo el sistema operativo representa los nombres de archivo [116] [117].

Para procesar texto línea a línea, `Files.newBufferedReader(path, UTF_8)` abre un `BufferedReader` con decodificación explícita. Para escribir texto gradualmente, use `Files.newBufferedWriter(path, UTF_8, opciones...)`. `InputStreamReader` es el puente entre bytes y caracteres y acepta un charset explícito; envolverlo en `BufferedReader` permite leer líneas de forma eficiente. Para datos binarios, use `Files.newInputStream` y `Files.newOutputStream`; no convierta esos bytes a `String` [113] [116].

```java
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.nio.file.Files;
import java.nio.file.Path;
public class CopiarBytes {
    public static void main(String[] args) throws IOException {
        Path origen = Path.of("entrada.bin");
        Path destino = Path.of("copia.bin");
        try (InputStream entrada = Files.newInputStream(origen);
             OutputStream salida = Files.newOutputStream(destino)) {
            entrada.transferTo(salida);
        }
        System.out.println("Copia terminada: " + destino);
    }
}
```

`transferTo` copia bytes desde Java 9. El ejemplo exige que `entrada.bin` exista y sea legible; una ruta incorrecta, permisos insuficientes o errores del dispositivo provocan `IOException`. Si se elige `Files.copy` y se desea reemplazar un destino existente, especifique `StandardCopyOption.REPLACE_EXISTING`; no agregue una opción de sobrescritura sin entender el efecto [108] [116].

**Buenas prácticas con rutas:** use `Path.resolve` en lugar de concatenar separadores manualmente; distinga `Files.exists`, `Files.isRegularFile` y `Files.isDirectory`; capture `IOException` en el nivel que pueda decidir si reintenta, informa o aborta. No confíe en una ruta aportada por usuario como si estuviera confinada automáticamente a una carpeta: valide la ubicación permitida y considere enlaces simbólicos y cambios concurrentes si el árbol de archivos es hostil. `normalize()` por sí solo no constituye una barrera de seguridad [117].

#### Codificación de texto: UTF-8 y compatibilidad

Un `String` representa texto Unicode, pero para guardarlo o transmitirlo hay que codificarlo como bytes. El mismo grupo de bytes puede producir texto distinto con un charset incorrecto. Por eso, declare `StandardCharsets.UTF_8` cuando el formato de intercambio lo exija. Desde JDK 18, UTF-8 es el charset predeterminado de la mayoría de las API estándar que dependían del charset por defecto; no debe extrapolarse esta regla a `System.out`, `System.err`, la consola, nombres de rutas, bibliotecas externas ni JDK antiguos. JEP 400 admite particularidades de configuración de implementaciones, y el comportamiento de terminal puede depender del vendor, la JVM, la configuración del proceso y el OS [115].

La API `Files` ya ofrece métodos de texto sin argumento `Charset` que especifican UTF-8, incluso antes de JDK 18. Aun así, pasar el charset explícitamente comunica el contrato y facilita detectar diferencias con APIs heredadas como ciertos constructores de `FileReader`, `FileWriter`, `Scanner` o `InputStreamReader`. No cambie `file.encoding` en tiempo de ejecución esperando reconfigurar las API que ya se inicializaron; para portabilidad, seleccione la codificación al crear el lector o escritor [115] [116].

Errores frecuentes son asumir que `char` equivale a un carácter Unicode completo, interpretar datos binarios como UTF-8 y mezclar codificaciones al leer y escribir. Un `char` Java es una unidad UTF-16 de 16 bits y algunos caracteres requieren dos unidades; recorra puntos de código cuando el problema lo requiera. Si un archivo de texto no es UTF-8, especifique su charset real; no “corrija” mojibake cambiando caracteres a mano [118].

#### `try`-with-resources y cierre de recursos

Un archivo abierto, un socket o un lector puede consumir recursos del sistema operativo. Una fuga aparece cuando un camino normal o excepcional omite cerrarlo. `try`-with-resources cierra automáticamente recursos que implementan `AutoCloseable`, incluso si ocurre una excepción, y los cierra en orden inverso al de su declaración. `IOException` es una excepción comprobada frecuente en I/O; puede propagarse declarando `throws IOException` o tratarse allí donde exista una recuperación útil [119].

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class LeerLineas {
    public static void main(String[] args) throws IOException {
        Path archivo = Path.of("datos", "saludo.txt");
        try (BufferedReader lector = Files.newBufferedReader(
                archivo, StandardCharsets.UTF_8)) {
            String linea;
            while ((linea = lector.readLine()) != null) {
                System.out.println(linea);
            }
        }
    }
}
```

Evite un `catch (Exception)` vacío que oculte fallos; añada contexto al mensaje sin perder la causa de la excepción. Los errores lanzados durante el cierre también pueden aparecer como excepciones suprimidas cuando ya había ocurrido otro fallo. No cierre recursos globales que el componente no posee (`System.in`, `System.out`, `System.err`) [119].

#### Serialización: concepto y formatos

**Serializar** es convertir datos u objetos a una representación que pueda almacenarse o transmitirse; **deserializar** es reconstruir datos desde esa representación. La elección del formato depende de interoperabilidad, tamaño, validación, evolución de esquema y restricciones de seguridad. JSON, XML y CSV son formatos de texto con distintas estructuras y no se vuelven equivalentes por ser serializables. Un formato de intercambio no valida por sí solo reglas del dominio: compruebe que los campos esperados existen, tienen tipo y cumplen límites y reglas de negocio [120] [121].

#### JSON: bibliotecas de terceros y API incubadora

Java SE no ofrece una API JSON general estable en las versiones GA cubiertas por esta sección. Para la mayoría de las aplicaciones, se añade una dependencia como **Jackson** o **Gson** a través de Maven o Gradle. Jackson proporciona análisis de flujo y mapeo de datos mediante `ObjectMapper`; Gson convierte objetos Java y representaciones JSON mediante `Gson`. Ambas son bibliotecas de terceros, no parte de Java SE, y sus versiones, opciones y reglas de mapeo se rigen por sus proyectos. En la fecha de corte, Maven Central muestra Jackson Databind 2.23.0; la guía oficial de Gson usa Gson 2.15.0 [122] [123] [124].

Dependencia Maven mínima para Jackson Databind:

```xml
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.23.0</version>
</dependency>
```

Dependencia Maven para Gson:

```xml
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.15.0</version>
</dependency>
```

Una aplicación puede elegir **una** de estas bibliotecas según compatibilidad, módulos, formato, rendimiento medido, configuración y política de dependencias. Mantenga versiones explícitas y actualizadas; evite versiones dinámicas en producción. En proyectos con Jackson, coordine versiones compatibles de `jackson-core`, `jackson-annotations` y `jackson-databind`, preferiblemente mediante el mecanismo de versiones recomendado por el proyecto. El ejemplo siguiente usa una clase Java convencional compatible con Java 11; valide después los valores según el dominio [122] [124].

```java
import com.fasterxml.jackson.databind.ObjectMapper;

public class JsonJackson {
    public static final class Persona {
        private String nombre;
        private int edad;

        public Persona() {}

        public Persona(String nombre, int edad) {
            this.nombre = nombre;
            this.edad = edad;
        }

        public String getNombre() { return nombre; }
        public void setNombre(String nombre) { this.nombre = nombre; }
        public int getEdad() { return edad; }
        public void setEdad(int edad) { this.edad = edad; }
    }

    public static void main(String[] args) throws Exception {
        ObjectMapper mapper = new ObjectMapper();
        Persona original = new Persona("Ada", 36);
        String json = mapper.writeValueAsString(original);
        Persona recuperada = mapper.readValue(json, Persona.class);
        System.out.println(json);
        System.out.println(recuperada.getNombre());
    }
}
```

Con la dependencia añadida, la salida prevista contiene los campos JSON `nombre` y `edad`, y a continuación imprime `Ada`; formato y orden de propiedades pueden variar según configuración. El JSON no contiene información suficiente para imponer automáticamente todas las reglas del objeto; compruebe nulos, rangos, campos inesperados y estructura según el contrato de la aplicación. No active el polimorfismo dinámico de tipos para JSON no confiable sin una política estricta de tipos permitidos [122] [124].

Con Gson, el mecanismo básico es `new Gson().toJson(objeto)` y `gson.fromJson(texto, Tipo.class)`. Con la clase `Persona` anterior, el cuerpo central es `Gson gson = new Gson(); String json = gson.toJson(original); Persona recuperada = gson.fromJson(json, Persona.class);`. Para colecciones genéricas, el tipo concreto debe conservarse mediante `TypeToken`; no espere que `List.class` reconstruya por sí sola el tipo de sus elementos. La guía del proyecto documenta que la instancia `Gson` puede reutilizarse, pero sus reglas sobre campos, nulos y clases locales deben revisarse, no asumirse como idénticas a Jackson [123].

Al corte, JEP 540 («Simple JSON API») figura integrada como **API incubadora para JDK 28**, y OpenJDK 28 ofrece acceso anticipado con GA planificada para marzo de 2027. Esto no equivale a una API estable disponible en el último JDK GA. Una API incubadora puede cambiar o desaparecer entre versiones; requiere el módulo incubador `jdk.incubator.json` y las opciones de módulo correspondientes. No la trate como alternativa estable ni la use sin aceptar expresamente esa dependencia de versión [125] [126].

#### XML: JAXP en Java SE y seguridad

Java SE incluye JAXP (*Java API for XML Processing*) en el módulo `java.xml`, con APIs como DOM, SAX, StAX, XPath y transformaciones. DOM construye un árbol en memoria y facilita navegación; SAX y StAX procesan eventos y son opciones para documentos grandes. El formato XML puede incorporar entidades y referencias a recursos externos. Con XML de origen no confiable, configure el procesador para no recuperar DTD o esquemas externos de forma inadvertida y aplique límites apropiados. Oracle advierte de riesgos XXE y de expansión de entidades; una opción de procesamiento seguro no sustituye la configuración y validación según el procesador y la aplicación [127].

```java
import java.io.InputStream;
import java.nio.file.Files;
import java.nio.file.Path;
import javax.xml.XMLConstants;
import javax.xml.parsers.DocumentBuilderFactory;
import org.w3c.dom.Document;

public class LeerXmlSeguro {
    public static void main(String[] args) throws Exception {
        Path ruta = Path.of("datos", "persona.xml");
        DocumentBuilderFactory fabrica = DocumentBuilderFactory.newInstance();
        fabrica.setFeature(XMLConstants.FEATURE_SECURE_PROCESSING, true);
        fabrica.setAttribute(XMLConstants.ACCESS_EXTERNAL_DTD, "");
        fabrica.setAttribute(XMLConstants.ACCESS_EXTERNAL_SCHEMA, "");
        fabrica.setXIncludeAware(false);
        fabrica.setExpandEntityReferences(false);

        try (InputStream entrada = Files.newInputStream(ruta)) {
            Document documento = fabrica.newDocumentBuilder().parse(entrada);
            System.out.println(documento.getDocumentElement().getTagName());
        }
    }
}
```

El ejemplo usa clases de Java SE y evita el acceso externo a DTD y esquemas. La capacidad de aplicar atributos y funciones puede depender del proveedor JAXP instalado; ante una configuración no reconocida, no ignore la excepción como si el parser hubiera quedado protegido. Para una carga real, valide el esquema cuando se necesite, aplique límites, y compruebe la configuración efectiva del parser usado [127].

#### CSV: texto delimitado con reglas de comillas

CSV (*Comma-Separated Values*) suele representar registros en filas y campos separados por comas, pero hay variaciones entre programas. RFC 4180 describe un formato común: campos con coma, comillas o saltos de línea deben entrecomillarse y las comillas interiores se duplican. Por ello, `linea.split(",")` no es un parser correcto en general: interpreta mal valores como `"Smith, Ada"` y campos entrecomillados con saltos de línea. Java SE ofrece herramientas de texto, pero no un parser CSV general; una biblioteca de terceros como Apache Commons CSV admite dialectos conocidos y debe configurarse según el archivo de destino [7] [128] [129].

Dependencia Maven de ejemplo para Apache Commons CSV 1.14.1, versión publicada en Maven Central consultada al corte (véase [130]):

```xml
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-csv</artifactId>
    <version>1.14.1</version>
</dependency>
```

```java
import java.io.Reader;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import org.apache.commons.csv.CSVFormat;
import org.apache.commons.csv.CSVParser;
import org.apache.commons.csv.CSVRecord;

public class LeerCsv {
    public static void main(String[] args) throws Exception {
        Path ruta = Path.of("datos", "personas.csv");
        CSVFormat formato = CSVFormat.RFC4180.builder()
                .setHeader()
                .setSkipHeaderRecord(true)
                .build();

        try (Reader lector = Files.newBufferedReader(ruta, StandardCharsets.UTF_8);
             CSVParser parser = formato.parse(lector)) {
            for (CSVRecord fila : parser) {
                String nombre = fila.get("nombre");
                int edad = Integer.parseInt(fila.get("edad"));
                System.out.println(nombre + ": " + edad);
            }
        }
    }
}
```

Para un archivo con contenido:

```csv
nombre,edad
"Ada, Lovelace",36
Grace,85
```

La salida prevista es `Ada, Lovelace: 36` y `Grace: 85`. El parseo de CSV entrega campos textuales: la conversión a `int` puede fallar y debe manejarse si el archivo puede contener datos incorrectos. Compruebe que el encabezado y el dialecto coinciden con la fuente; si el CSV se abre en una hoja de cálculo, considere además el riesgo de inyección de fórmulas en campos que empiezan con caracteres interpretados como fórmulas [128] [129].

#### Serialización nativa de Java: legado, compatibilidad y seguridad

La serialización nativa convierte grafos de objetos a un formato binario propio de Java mediante `Serializable`, `ObjectOutputStream` y `ObjectInputStream`. Se diseñó para reconstruir objetos Java con información de clase y referencias; no es JSON, no es un formato independiente del lenguaje y no resulta una elección adecuada por defecto para APIs públicas, archivos de larga duración o datos que deban ser consumidos por sistemas heterogéneos. Cambios en las clases, `serialVersionUID`, compatibilidad y métodos personalizados como `readObject` influyen en la evolución del formato [131].

**Estado y advertencia de deprecación.** Al corte de esta guía, las API de serialización nativa siguen presentes en Java SE 27. No debe confundirse la JEP 154, una propuesta para eliminar serialización que OpenJDK marca como *Withdrawn*, con una deprecación adoptada: no se afirma aquí que `Serializable`, `ObjectInputStream` u `ObjectOutputStream` estén deprecados en Java 27. Esto tampoco significa que el mecanismo sea recomendado para datos nuevos: Oracle lo describe como peligroso ante datos no confiables y aconseja evitar deserializarlos. La compatibilidad o el soporte concreto de cada JDK siguen sujetos al proveedor y su política [132] [133] [134].

Ejemplo didáctico de round-trip local; solo se debe usar con un archivo controlado por la propia aplicación:

```java
import java.io.IOException;
import java.io.ObjectInputFilter;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.Serializable;
import java.nio.file.Files;
import java.nio.file.Path;

public class SerializacionNativa {
    static final class Perfil implements Serializable {
        private static final long serialVersionUID = 1L;

        private final String nombre;
        private final int nivel;

        Perfil(String nombre, int nivel) {
            this.nombre = nombre;
            this.nivel = nivel;
        }

        @Override
        public String toString() {
            return nombre + " (nivel " + nivel + ")";
        }
    }

    public static void main(String[] args) throws IOException, ClassNotFoundException {
        Path ruta = Path.of("perfil.bin");
        Perfil perfil = new Perfil("Ada", 3);

        try (ObjectOutputStream salida = new ObjectOutputStream(
                Files.newOutputStream(ruta))) {
            salida.writeObject(perfil);
        }

        try (ObjectInputStream entrada = new ObjectInputStream(
                Files.newInputStream(ruta))) {
            entrada.setObjectInputFilter(ObjectInputFilter.Config.createFilter(
                    "SerializacionNativa$Perfil;java.base/*;!*"));
            Object valor = entrada.readObject();
            if (!(valor instanceof Perfil recuperado)) {
                throw new IOException("Tipo inesperado en el archivo");
            }
            System.out.println(recuperado);
        }
    }
}
```

La salida prevista es `Ada (nivel 3)`. El filtro restringe clases aceptadas y reduce riesgos de grafos excesivos; adapte el patrón a las clases realmente necesarias y pruebe la política en el contexto real. Los filtros de serialización no están necesariamente activados por defecto; declararlos en un ejemplo no justifica aceptar entradas de red o archivos de terceros. Si un flujo no es de confianza, la recomendación principal es no deserializarlo. Si no puede evitarse, use una lista permitida estricta, límites de profundidad, bytes, referencias y arreglos, y valide invariantes después de leer. Los filtros reducen la superficie de ataque, no convierten el formato en seguro por sí solos [133] [135].

Errores frecuentes con serialización nativa incluyen asumir que `transient` cifra u oculta secretos, asumir que `serialVersionUID` garantiza compatibilidad semántica y cargar con `ObjectInputStream` bytes de procedencia desconocida. `transient` no ofrece seguridad criptográfica; no serialice credenciales; no use la serialización nativa como sustituto de un esquema validable. Para nuevas integraciones, considere JSON/XML/CSV u otro formato mantenido con contrato y validación explícitos, seleccionando una biblioteca con mantenimiento activo [133] [135].

#### Errores frecuentes y recomendaciones de conjunto

- **Texto corrupto:** lector y escritor usan charsets distintos. Declare la codificación pactada, habitualmente UTF-8, en ambos extremos.
- **Excepción al leer un número:** entrada vacía, mal formada o fuera del rango del tipo. Valide el formato y el rango; no dependa de `nextInt()` sin comprobar el token.
- **`nextLine()` devuelve vacío:** un método de lectura por tokens dejó pendiente el resto de la línea. Lea líneas de forma consistente o consuma el separador de manera explícita.
- **Archivo sobrescrito sin querer:** opciones de escritura truncan de forma predeterminada en ciertas llamadas. Use opciones que expresen si se crea, agrega o reemplaza.
- **Archivo cargado completo innecesariamente:** `readString` y `readAllBytes` conservan el contenido en memoria. Procese por líneas o bloques en archivos grandes.
- **Fuga de recursos:** el cierre no ocurre en alguna rama. Use `try`-with-resources para archivos y recursos que sean propiedad del método.
- **CSV dividido con `split`:** los campos entrecomillados pueden contener separadores, comillas o saltos de línea. Elija un parser configurado para el dialecto real.
- **Parser XML expuesto:** el procesador puede resolver entidades externas o consumir recursos excesivos. Configure JAXP y limite entradas según la guía de seguridad.
- **JSON tratado como modelo validado:** parsear solo establece sintaxis y tipos representados. Añada validación de esquema y dominio.
- **Deserialización insegura:** la entrada binaria nativa puede inducir la creación de objetos con efectos secundarios. No la use con datos no confiables.
- **Salida y error confundidos:** `System.out` y `System.err` se redirigen por separado. Dirija resultados y diagnósticos al canal apropiado y use *logging* cuando necesite registro estructurado.

Para una aplicación profesional, acuerde explícitamente el charset, valide las entradas en la frontera, seleccione una API según tamaño y estructura, documente las opciones que modifican archivos, mantenga dependencias externas actualizadas y registre errores con contexto sin filtrar secretos. Las salidas previstas de los ejemplos ilustran el comportamiento esperado; no implican que los programas se hayan compilado o ejecutado durante la elaboración de esta sección.

## 10. Concurrencia y paralelismo

Los ejemplos ejecutables de la API estable marcados para `--release 21` se compilaron y ejecutaron con OpenJDK 21.0.13.1 disponible en este entorno. El ejemplo de Structured Concurrency es preview de JDK 27 y no se validó aquí, porque no se dispone de ese JDK.

#### Concurrencia, paralelismo y procesos

**Concurrencia** es la capacidad de hacer progresar varias tareas durante periodos de tiempo que se solapan. Esto no exige que se ejecuten exactamente al mismo tiempo: un único núcleo puede alternar entre ellas. **Paralelismo** es ejecutar tareas simultáneamente, por ejemplo en núcleos distintos. El paralelismo puede reducir el tiempo de trabajo CPU-bound si hay recursos disponibles, pero la concurrencia también resulta útil para coordinar muchas esperas de entrada/salida [136].

Un **proceso** tiene su propio espacio de direcciones y recursos del sistema operativo. Un **hilo** es una secuencia de ejecución dentro de un proceso; los hilos de un proceso comparten memoria del montón, pero cada uno mantiene su propio flujo de ejecución y contexto. En Java, la JVM permite que varios hilos ejecuten código concurrentemente. Un programa puede usar concurrencia sin paralelismo y paralelismo sin que ello haga automáticamente más eficiente cada operación [137].

La programación asíncrona organiza el resultado de una operación para procesarlo cuando esté listo, en lugar de bloquear inmediatamente al llamador. No es sinónimo de paralelismo: una `CompletableFuture` puede completar en el mismo hilo que la crea, en otro hilo o después de una operación concurrente. La plataforma ofrece hilos, ejecutores y etapas asíncronas; el estilo de programación lo determina el problema y la API elegida [136] [138].

#### Hilos: `Thread`, `Runnable` e interrupción

Un `Thread` representa un hilo de ejecución. El método `start()` programa un hilo nuevo y hace que este invoque `run()`; llamar directamente a `run()` ejecuta el método en el hilo actual y **no** crea otro hilo. `Runnable` representa una tarea sin resultado; `Callable<T>` representa una tarea que puede producir un resultado y lanzar excepciones comprobadas. En aplicaciones ordinarias conviene delegar la gestión de hilos en un ejecutor, en vez de crear y administrar manualmente muchos hilos [137] [139].

```java
// Archivo: HiloBasico.java
public class HiloBasico {
    public static void main(String[] args) throws InterruptedException {
        Thread trabajador = Thread.ofPlatform()
                .name("trabajador")
                .start(() -> System.out.println("Trabajo en " + Thread.currentThread().getName()));

        trabajador.join();
        System.out.println("El trabajador terminó");
    }
}
```

Compilación y ejecución en JDK 21 o posterior:

```bash
javac --release 21 HiloBasico.java
java HiloBasico
```

Salida esperada:

```text
Trabajo en trabajador
El trabajador terminó
```

`join()` espera a que termine el hilo y establece una relación de visibilidad: las acciones del hilo que termina ocurren antes de que otro hilo retorne correctamente de `join()`. Si una operación de espera lanza `InterruptedException`, no se debe ignorar la interrupción; propaga la excepción cuando sea posible o restaura el estado con `Thread.currentThread().interrupt()` si el método no puede propagarla [137] [140].

La interrupción es una señal cooperativa, no una terminación forzada. Un hilo debe reaccionar a esa señal en las operaciones bloqueantes que la admiten o consultar su estado en puntos seguros. No uses métodos obsoletos como `Thread.stop()` para cancelar tareas. La terminación forzada puede dejar invariantes y recursos en un estado incoherente [137].

#### `ExecutorService` y `Future`

`Executor` desacopla el envío de una tarea de la política que decide cuándo y dónde ejecutarla. `ExecutorService` amplía el contrato con gestión de tareas y cierre ordenado. Puede recibir `Runnable` mediante `execute()` o tareas `Runnable`/`Callable` con `submit()`. Este último devuelve un `Future<T>`, objeto que permite consultar finalización, cancelar e intentar obtener el resultado. `Future.get()` espera si es necesario; puede lanzar `InterruptedException` o `ExecutionException` si la tarea falló [139] [141].

El ejecutor es dueño del ciclo de vida del trabajador. Hay que cerrarlo para rechazar nuevas tareas y completar las ya aceptadas. Desde Java 19, `ExecutorService` es `AutoCloseable`, así que `try` con recursos proporciona una forma directa de cerrarlo. `shutdownNow()` intenta interrumpir tareas y descartar tareas pendientes, pero no garantiza detener código que no responda a interrupciones [139] [141].

```java
// Archivo: TareasConFuturo.java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class TareasConFuturo {
    public static void main(String[] args) throws InterruptedException, ExecutionException {
        try (ExecutorService ejecutor = Executors.newFixedThreadPool(2)) {
            Callable<Integer> tarea = () -> 20 + 22;
            Future<Integer> resultado = ejecutor.submit(tarea);
            System.out.println("Resultado: " + resultado.get());
        }
    }
}
```

Comandos y salida esperada:

```bash
javac --release 21 TareasConFuturo.java
java TareasConFuturo
```

```text
Resultado: 42
```

Un pool de tamaño fijo es apropiado cuando se desea limitar la cantidad de tareas ejecutándose a la vez. El tamaño adecuado depende de si predominan tareas CPU-bound o esperas de I/O, así como de los límites externos, como conexiones disponibles. No uses un pool sin límite o un tamaño arbitrario sin medir carga, memoria y latencia. Los ejecutores de la fábrica `Executors` no son todos iguales: por ejemplo, un pool fijo limita los trabajadores, pero normalmente usa una cola de tareas sin límite, por lo que aún puede acumular trabajo pendiente [139].

`Future.cancel(true)` solicita la cancelación y puede interrumpir el hilo de la tarea si la implementación lo conoce; no equivale a detenerla a la fuerza. Diseña las tareas para que respondan a interrupciones, liberen recursos y terminen con seguridad. Capturar `InterruptedException` y continuar como si nada borra la señal y suele romper la cancelación. Si se captura para traducirla a otro resultado o excepción, restaura el estado de interrupción cuando corresponda [137] [141].

#### `CompletableFuture` y composición asíncrona

`CompletableFuture<T>` implementa `Future<T>` y `CompletionStage<T>`. Permite crear etapas dependientes con operaciones como `thenApply` (transformar resultado), `thenCompose` (encadenar una operación asíncrona sin anidar futuros) y `thenCombine` (combinar resultados independientes). `exceptionally`, `handle` y `whenComplete` proporcionan distintos modos de tratar terminaciones excepcionales. Los métodos sin sufijo `Async` pueden ejecutar la continuación en el hilo que completa la etapa; las variantes `Async` sin ejecutor explícito suelen usar `ForkJoinPool.commonPool()` [138].

```java
// Archivo: EtapasAsincronas.java
import java.util.concurrent.CompletableFuture;

public class EtapasAsincronas {
    public static void main(String[] args) {
        CompletableFuture<Integer> calculo = CompletableFuture
                .supplyAsync(() -> 21)
                .thenApplyAsync(numero -> numero * 2);

        System.out.println("Resultado: " + calculo.join());
    }
}
```

Comandos y salida esperada:

```bash
javac --release 21 EtapasAsincronas.java
java EtapasAsincronas
```

```text
Resultado: 42
```

El valor es determinista, aunque no se debe inferir del ejemplo en qué hilo se ejecutó cada etapa. Para controlar la política de ejecución, proporciona un `Executor` explícito a los métodos `*Async`. Evita bloquear con `join()` o `get()` dentro de un hilo que también necesita completar las dependencias; una composición incorrecta puede agotar el pool o producir interbloqueo. `CompletableFuture.cancel()` representa una finalización excepcional y no necesariamente controla ni detiene el cálculo que produciría el valor [138].

#### Hilos virtuales desde Java 21

Un hilo virtual es un `Thread` ligero gestionado por el runtime Java, no un hilo 1:1 dedicado del sistema operativo. Los hilos virtuales permiten sostener muchas tareas concurrentes que pasan buena parte del tiempo bloqueadas, sobre todo en I/O, manteniendo un estilo de código secuencial. Son hilos reales de Java, no tareas asíncronas ni núcleos de CPU adicionales. No están diseñados para acelerar una tarea intensiva de CPU: el paralelismo de CPU sigue limitado por los núcleos disponibles [86] [137].

La API se finalizó en JDK 21. Un patrón habitual es crear un hilo virtual por tarea con `Executors.newVirtualThreadPerTaskExecutor()`, sin intentar crear un pool de hilos virtuales. Si se debe limitar una dependencia —por ejemplo, una base de datos—, limita ese recurso mediante un semáforo, un pool de conexiones u otro mecanismo explícito; reutilizar hilos virtuales para limitar la concurrencia reintroduce una restricción distinta de la capacidad de los hilos [86].

```java
// Archivo: HilosVirtuales.java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class HilosVirtuales {
    public static void main(String[] args) throws Exception {
        try (ExecutorService ejecutor = Executors.newVirtualThreadPerTaskExecutor()) {
            Future<String> saludo = ejecutor.submit(
                    () -> "Ejecutando en hilo virtual: " + Thread.currentThread().isVirtual());
            System.out.println(saludo.get());
        }
    }
}
```

Comandos y salida esperada:

```bash
javac --release 21 HilosVirtuales.java
java HilosVirtuales
```

```text
Ejecutando en hilo virtual: true
```

La API es estándar desde Java 21, pero aspectos como el scheduler, la interacción con I/O nativo y los diagnósticos dependen de la implementación de JVM y del sistema operativo. En JDK 21–23, algunos bloqueos dentro de código `synchronized` podían fijar (*pin*) el hilo virtual a su hilo portador. JEP 491 cambió la implementación de HotSpot en JDK 24 para permitir que un hilo virtual se desmonte también en casi todos esos casos; quedan escenarios de pinning, como ciertas llamadas nativas o el uso de la API Foreign Function & Memory. Por tanto, no se debe aplicar a todos los JDK/vendors una misma recomendación operativa sobre pinning; diagnostica la JVM concreta con sus herramientas [137] [142].

No hagas tareas CPU-bound largas en millones de hilos virtuales esperando ganar velocidad. Evita mantener monitores o bloqueos durante I/O prolongada cuando ello reduzca paralelismo útil, y no confundas hilos virtuales ilimitados en número práctico con recursos externos ilimitados. Hilos virtuales son especialmente útiles en servidores con muchas solicitudes bloqueantes; una biblioteca bloqueante nativa puede no beneficiarse de la misma manera que I/O implementada para integrarse con el runtime [86] [137].

#### Structured Concurrency: API preview y versiones

La concurrencia estructurada agrupa subtareas relacionadas bajo un ámbito léxico: el código padre abre un ámbito, lanza subtareas, espera su desenlace y cierra el ámbito. El objetivo es coordinar la cancelación, errores, finalización y observabilidad como una sola unidad de trabajo. No reemplaza `ExecutorService` ni `Future`; sirve a patrones donde una operación padre crea tareas hijas que deben tener vidas acotadas al padre [87].

**Aviso de versión:** a la fecha de corte, JEP 533 entrega Structured Concurrency como **séptimo preview en JDK 27**. No es API estable y su diseño ha cambiado repetidamente entre versiones; no traslades sin revisión ejemplos de los previews de JDK 21–26. Para probarlo hace falta JDK 27 compatible y compilar/ejecutar con `--enable-preview` y `--release 27`. El fragmento siguiente refleja la API propuesta en JEP 533; no se ha compilado en este entorno, que dispone de JDK 21 [143] [87] [144].

```java
// Archivo: TareasEstructuradas.java — API preview de JDK 27
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.StructuredTaskScope;
import java.util.concurrent.StructuredTaskScope.Joiner;

public class TareasEstructuradas {
    static <T> List<T> ejecutarTodas(List<Callable<T>> tareas)
            throws InterruptedException, ExecutionException {
        try (var scope = StructuredTaskScope.open(Joiner.<T>allSuccessfulOrThrow())) {
            tareas.forEach(scope::fork);
            return scope.join();
        }
    }

    public static void main(String[] args) throws InterruptedException, ExecutionException {
        var resultados = ejecutarTodas(List.of(() -> "A", () -> "B"));
        System.out.println("Tareas completas: " + resultados.size());
    }
}
```

Con JDK 27:

```bash
javac --enable-preview --release 27 TareasEstructuradas.java
java --enable-preview TareasEstructuradas
```

El `main` muestra una ejecución completa y cuenta los resultados, sin depender del orden en que acaben las subtareas. En `allSuccessfulOrThrow()`, si todas las subtareas terminan bien, `join()` devuelve una lista con resultados; un fallo provoca una excepción y se cancelan las demás tareas según la política del ámbito. La salida esperada es `Tareas completas: 2`. Comprueba el texto y los métodos exactos en la documentación del JDK instalado: en una versión posterior pueden cambiar o desaparecer. Las features preview no deben usarse como base de una interfaz pública estable sin aceptar explícitamente el coste de migración [87] [144].

#### Sincronización: `synchronized`, `Lock` y `volatile`

La sincronización protege invariantes compartidas y coordina la visibilidad entre hilos. El bloque o método `synchronized` adquiere el monitor del objeto indicado —o el monitor de la clase en un método estático sincronizado— y lo libera al salir, incluso por excepción. Un solo hilo puede poseer el mismo monitor a la vez. Mantén la sección crítica pequeña, protege el mismo estado siempre con la misma disciplina y no invoques callbacks o servicios externos desconocidos mientras mantienes un monitor [140].

`Lock`, incluido `ReentrantLock`, ofrece operaciones adicionales como adquisición interrumpible, espera con límite, intento de adquisición y condiciones explícitas. A cambio, la liberación no es automática: empareja cada `lock()` con `unlock()` en `finally`. La equidad puede reducir variación en espera, pero suele disminuir rendimiento y no garantiza que el planificador del sistema operativo sea justo [145].

```java
// Archivo: ContadorSeguro.java
import java.util.concurrent.locks.ReentrantLock;

public class ContadorSeguro {
    private final ReentrantLock lock = new ReentrantLock();
    private int valor;

    public void incrementar() {
        lock.lock();
        try {
            valor++;
        } finally {
            lock.unlock();
        }
    }

    public int obtener() {
        lock.lock();
        try {
            return valor;
        } finally {
            lock.unlock();
        }
    }

    public static void main(String[] args) {
        ContadorSeguro contador = new ContadorSeguro();
        contador.incrementar();
        contador.incrementar();
        System.out.println(contador.obtener());
    }
}
```

Salida esperada: `2`. En este ejemplo se usa un bloqueo explícito para ilustrar el patrón `try/finally`; si basta exclusión mutua simple, `synchronized` suele ser más directo y menos propenso a olvidar la liberación [145].

`volatile` garantiza visibilidad y orden para lecturas/escrituras del campo conforme al modelo de memoria, pero no convierte una secuencia de operaciones en una unidad atómica. Por ejemplo, `volatile int contador; contador++` sigue siendo lectura, suma y escritura y puede perder incrementos. Para una variable individual use `AtomicInteger`; para varias variables que deban cambiar como una sola unidad, use un bloqueo o rediseñe el estado [140] [146].

#### Variables atómicas

Las clases de `java.util.concurrent.atomic`, como `AtomicInteger`, `AtomicLong` y `AtomicReference`, ofrecen operaciones atómicas para un valor individual. Métodos como `incrementAndGet()` o `compareAndSet()` evitan la carrera de una actualización aislada. El paquete también incluye acumuladores como `LongAdder`, útiles para contadores muy disputados donde se consulta el resultado agregado, pero no sustituye a un bloqueo cuando hay invariantes compuestas [146].

```java
// Archivo: ContadorAtomico.java
import java.util.concurrent.atomic.AtomicInteger;

public class ContadorAtomico {
    public static void main(String[] args) {
        AtomicInteger visitas = new AtomicInteger();
        visitas.incrementAndGet();
        visitas.addAndGet(4);
        System.out.println(visitas.get());
    }
}
```

Salida esperada: `5`. Las operaciones atómicas no hacen automáticamente seguros otros campos relacionados. No conviertas un objeto entero en una colección de atomics si una única sección crítica expresa mejor la invariante. Además, una función de actualización como `updateAndGet` puede volver a ejecutarse ante contención: su función debe evitar efectos secundarios no repetibles [146].

#### Modelo de memoria y relación *happens-before*

El modelo de memoria de Java define qué escrituras de un hilo pueden observar otros hilos y qué reordenamientos son legales. Una relación **happens-before** ordena dos acciones: si una acción ocurre antes que otra bajo esta relación, sus efectos son visibles y están ordenados para la segunda. No equivale a que el sistema operativo haya ejecutado físicamente una instrucción en ese instante; es una garantía observable del lenguaje [140].

Reglas prácticas importantes:

- El orden del programa dentro de un solo hilo contribuye a *happens-before*.
- Desbloquear un monitor ocurre antes de una adquisición posterior del mismo monitor (`synchronized`).
- Escribir un campo `volatile` ocurre antes de lecturas posteriores de ese mismo campo.
- Llamar `Thread.start()` ocurre antes de las acciones del hilo iniciado; las acciones del hilo ocurren antes del retorno exitoso de `join()` en otro hilo.
- Enviar una tarea a un `ExecutorService` ocurre antes de las acciones de esa tarea; las acciones de la tarea ocurren antes de recuperar su resultado con `Future.get()` [140] [139] [141].

El acceso concurrente conflictivo a un dato compartido, con al menos una escritura y sin relación *happens-before* entre accesos, forma una **data race**. El efecto no se corrige por usar un procesador de un solo núcleo ni por observar que las pruebas “siempre funcionan” en una máquina. Programas correctamente sincronizados reciben garantías de consistencia secuencial según la especificación, pero eso por sí solo no demuestra que el algoritmo cumpla el objetivo funcional [140].

#### Condiciones de carrera y errores compuestos

Una **condición de carrera** (*race condition*) aparece cuando el resultado depende del intercalado de tareas. El caso clásico es una actualización compuesta: dos hilos leen `contador == 0`, ambos calculan `1` y escriben `1`, aunque debían sumar dos veces. La operación `contador++` no es atómica. Una data race es una condición formal del modelo de memoria; una condición de carrera es una categoría algorítmica más amplia: puede haber carrera lógica incluso con operaciones atómicas individuales si varias operaciones no se coordinan como conjunto [140] [146].

```java
// Incorrecto si varios hilos comparten esta instancia:
class ContadorInseguro {
    private int valor;
    void incrementar() { valor++; }
}

// Corrección sencilla:
class ContadorSincronizado {
    private int valor;
    synchronized void incrementar() { valor++; }
    synchronized int obtener() { return valor; }
}
```

No hay una salida concreta que se pueda prometer para la versión insegura; el resultado dependerá del orden de ejecución y del entorno. Para corregir el problema, protege lectura y escritura con el mismo bloqueo, sustituye el campo por una operación atómica adecuada o evita compartir estado mutable. `HashMap` no se vuelve seguro por añadir `volatile` a la referencia que lo contiene: la estructura y sus operaciones siguen necesitando coordinación [140] [146] [147].

#### Interbloqueos y progreso

Un **interbloqueo** (*deadlock*) sucede cuando dos o más hilos esperan indefinidamente por recursos que retienen unos a otros. Un patrón típico es que el hilo A toma el bloqueo X y espera Y, mientras B toma Y y espera X. También hay riesgos relacionados como inanición —un hilo no obtiene recursos durante mucho tiempo— y *livelock*, donde los hilos siguen reaccionando pero no avanzan [145].

Para reducir el riesgo, define un orden global de adquisición de bloqueos y respétalo; mantén bloqueos el mínimo tiempo necesario; evita ejecutar I/O bloqueante mientras sostienes un bloqueo compartido; usa `tryLock` con timeout si el flujo puede recuperarse y considera interrupción/cancelación. Los timeouts detectan espera excesiva, pero no sustituyen el diseño de una política de recuperación coherente. Al depurar, usa un volcado de hilos (`jcmd <pid> Thread.print` o herramientas del IDE) para localizar hilos bloqueados y los bloqueos que esperan; el comando y el formato varían por JDK/OS [145] [148].

#### Colecciones concurrentes

Una colección concurrente brinda garantías de acceso entre hilos sin requerir que el llamador proteja cada método con un único bloqueo externo. No vuelve atómico cualquier secuencia de llamadas separadas; elija operaciones compuestas de la propia API cuando estén disponibles. Las colecciones de `java.util.concurrent` incluyen mapas, colas bloqueantes y no bloqueantes, conjuntos y listas de copia en escritura [136].

- `ConcurrentHashMap<K,V>` admite lecturas y actualizaciones concurrentes y no permite claves ni valores `null`. Los recorridos son débilmente consistentes: reflejan elementos en algún punto desde el comienzo del recorrido, no una instantánea indivisible de todo el mapa. Para inicializar y actualizar por clave, usa `computeIfAbsent`, `merge` u operaciones de `ConcurrentMap` en vez de hacer `get` y `put` separados [147].
- `BlockingQueue` como `ArrayBlockingQueue` o `LinkedBlockingQueue` coordina productores y consumidores; `put` y `take` pueden bloquear cuando la cola está llena o vacía. Es una herramienta de comunicación entre hilos del mismo proceso.
- `ConcurrentLinkedQueue` es una cola FIFO concurrente no bloqueante. `CopyOnWriteArrayList` facilita lecturas y recorridos frecuentes con pocas escrituras, porque cada modificación copia el arreglo; no es apropiada para actualizaciones intensivas [136].

```java
// Archivo: FrecuenciasConcurrentes.java
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.atomic.LongAdder;

public class FrecuenciasConcurrentes {
    public static void main(String[] args) {
        var frecuencias = new ConcurrentHashMap<String, LongAdder>();
        frecuencias.computeIfAbsent("java", clave -> new LongAdder()).increment();
        frecuencias.computeIfAbsent("java", clave -> new LongAdder()).increment();
        System.out.println(frecuencias.get("java").sum());
    }
}
```

Salida esperada: `2`. `computeIfAbsent` evita la carrera entre comprobar la ausencia e insertar el valor asociado. La función de mapeo debe ser breve y no debe intentar modificar recursivamente el mismo mapa para claves que interfieran. `LongAdder` distribuye contención del contador; su valor agregado durante actualizaciones concurrentes es una observación de progreso, no una transacción global [146] [147].

Cuando dos procesos necesitan comunicarse, las colecciones concurrentes no bastan: residen en una JVM y no comparten memoria con otros procesos. Usa mecanismos de IPC como sockets, pipes, archivos acordados o procesos iniciados con `ProcessBuilder`, con protocolos, límites y manejo de fallos apropiados [137].

#### Streams paralelos

Un `Stream` procesa elementos de una fuente mediante operaciones intermedias y una operación terminal. `parallelStream()` o `parallel()` solicita que la canalización pueda procesarse en paralelo; no crea necesariamente un hilo por elemento y no garantiza acelerar el trabajo. Puede ser útil en datos suficientemente grandes, con operaciones independientes, divisibles y con reducción eficiente. La implementación de streams paralelos de OpenJDK/Oracle suele emplear `ForkJoinPool.commonPool()`, pero el rendimiento depende de la fuente, el coste de cada operación, la carga del pool y la JVM [149] [150].

```java
// Archivo: SumaParalela.java
import java.util.stream.LongStream;

public class SumaParalela {
    public static void main(String[] args) {
        long suma = LongStream.rangeClosed(1, 1_000_000)
                .parallel()
                .sum();
        System.out.println(suma);
    }
}
```

Comandos y salida esperada:

```bash
javac --release 21 SumaParalela.java
java SumaParalela
```

```text
500000500000
```

La suma es una reducción asociativa adecuada para dividir y combinar. No uses estado mutable compartido dentro de `map`, `filter` o `forEach`, y evita asumir orden de ejecución o de efectos secundarios. `forEachOrdered` preserva orden de encuentro en el resultado, pero puede reducir el paralelismo. Un stream paralelo puede ser más lento por el coste de partición y coordinación; mide con datos representativos y compara contra la versión secuencial. No uses streams paralelos para reemplazar un sistema de tareas de I/O con límites y cancelación explícitos [149] [150].

#### Errores frecuentes y prácticas profesionales

- **Llamar a `run()` pensando que inicia otro hilo.** Usa `start()` o, preferiblemente, envía la tarea a un ejecutor.
- **Compartir un contador o `ArrayList` mutable sin coordinación.** Encapsula el estado, usa un bloqueo o una colección concurrente adecuada; evita compartirlo si puede expresarse como valores inmutables.
- **Suponer que `volatile` hace atómica una operación compuesta.** Usa `AtomicInteger` para una variable, y un lock para invariantes de varios campos.
- **Ignorar excepciones de tareas.** Recupera el `Future`, llama `get()` o compón una etapa de error; de lo contrario, el fallo puede quedar oculto al hilo que envió la tarea.
- **No cerrar el ejecutor o usar un pool inadecuado.** Establece dueño claro, política de cierre, capacidad y límites; evita bloquear el hilo de un pool esperando trabajo que solo ese mismo pool puede ejecutar.
- **Cancelar como si fuese detener.** Propaga y atiende interrupciones. Diseña límites de tiempo y limpieza de recursos; `cancel(true)` es una petición cooperativa.
- **Bloquear en orden inconsistente o dentro de una llamada externa.** Define orden global, reduce la sección crítica y evita invocaciones externas bajo lock.
- **Usar `parallelStream()` solo por tener una colección grande.** Comprueba independencia, tamaño, divisibilidad, coste de coordinación y efectos secundarios; mide antes de adoptarlo.
- **Aplicar recetas de Java 21 a cualquier versión/JVM.** Comprueba la versión de compilador y runtime, la implementación de JVM y el sistema operativo cuando dependas de comportamiento de scheduler, I/O, afinidad o diagnósticos [137] [139] [86] [137] [149].

En producción, prefiere abstracciones de nivel más alto hasta que una necesidad medida exija gestión explícita de hilos. Expón límites de concurrencia en recursos reales, registra métricas de cola y latencia, define estrategia de cancelación y prueba fallos y cierres. Trata el estado compartido como una decisión arquitectónica, no como un detalle que se arregla al final con `synchronized`.

## 11. Manejo de errores y depuración

Un programa puede fallar antes de iniciarse, durante su ejecución o sin producir ninguna señal técnica de fallo. Para diagnosticarlo conviene distinguir **error de compilación**, **excepción o error de ejecución** y **defecto lógico**. Java dispone de excepciones como mecanismo uniforme para comunicar condiciones excepcionales y transferir el control a un manejador; cada excepción es un objeto de `Throwable` o de una subclase [55] [56].

#### Clases de errores

**Error de compilación.** El compilador (`javac`) no puede aceptar el código o generar las clases solicitadas. Puede deberse a sintaxis incorrecta, tipos incompatibles, un nombre no resuelto, una llamada a método inválida o a que una excepción comprobada no se captura ni declara. El código con estos diagnósticos no se ejecuta como programa. La obligación de tratar excepciones comprobadas es una regla de compilación, no una excepción que ocurra durante la ejecución [55].

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

class LecturaIncorrecta {
    String leer() {
        return Files.readString(Path.of("datos.txt")); // No compila: IOException no tratada.
    }
}
```

Para resolverlo, el método debe capturar la excepción cuando sabe recuperarse o declararla para que el llamador decida:

```java
String leer() throws IOException {
    return Files.readString(Path.of("datos.txt"));
}
```

**Excepción de ejecución.** Se produce mientras corre un programa ya compilado. Puede ser una condición prevista por una operación (`IOException`, `NumberFormatException`) o una condición de programación (`NullPointerException`, `IndexOutOfBoundsException`). Si nadie la captura en la pila de llamadas del hilo, normalmente llega al manejador no capturado de la JVM; en una aplicación corriente se muestra un diagnóstico en la salida de error y puede terminar el hilo o el proceso, según el contexto [55] [56].

**Defecto lógico.** El programa compila y puede terminar con normalidad, pero obtiene una respuesta incorrecta: por ejemplo, calcular el subtotal multiplicando el precio por `cantidad - 1`. La JVM no puede deducir el resultado de negocio esperado. Se descubre mediante pruebas, depuración, revisión de requisitos, métricas o comparación con resultados conocidos, no necesariamente capturando una excepción.

No se deben mezclar estas categorías con la jerarquía de Java: “error de compilación” y “error lógico” son clasificaciones de defectos; `java.lang.Error` es una clase concreta dentro de `Throwable` que representa fallos graves para los que normalmente no se espera recuperación ordinaria [55] [56].

#### Jerarquía `Throwable`: comprobadas y no comprobadas

La jerarquía esencial es:

```text
Object
└── Throwable
    ├── Error                         no comprobada
    │   ├── OutOfMemoryError
    │   ├── StackOverflowError
    │   └── LinkageError
    └── Exception
        ├── RuntimeException          no comprobada
        │   ├── NullPointerException
        │   ├── IllegalArgumentException
        │   └── IndexOutOfBoundsException
        └── otras subclases de Exception  comprobadas
            ├── IOException
            └── SQLException
```

Una excepción **comprobada** (*checked exception*) es una subclase de `Throwable` que no pertenece a `RuntimeException` ni a `Error`. El compilador exige capturarla o declararla en `throws` cuando el análisis de flujo determina que la operación puede producirla. `IOException` y `SQLException` son ejemplos habituales. Una excepción **no comprobada** (*unchecked exception*) es una subclase de `RuntimeException` o de `Error`; no exige captura ni declaración [55] [56].

La distinción no significa que toda excepción comprobada sea recuperable ni que toda no comprobada sea imposible de tratar. Es una decisión de diseño del contrato: las comprobadas hacen explícita una condición que el llamador podría resolver; las no comprobadas suelen señalar un argumento o estado inválido, un fallo de programación o una condición grave del entorno. No captures `Error` de forma general para “mantener vivo” el proceso: la JVM puede estar sin recursos o en estado no recuperable.

| Categoría | Ejemplos | Regla | Tratamiento habitual |
|---|---|---|---|
| Comprobada | `IOException`, `SQLException` | Capturar o declarar | Recuperar, reintentar con límites, traducir conservando causa o propagar. |
| No comprobada derivada de `RuntimeException` | `IllegalArgumentException`, `NullPointerException` | Sin obligación de captura/declaración | Corregir contrato, validar entradas y estados; capturar solo si hay una recuperación concreta. |
| `Error` | `OutOfMemoryError`, `LinkageError` | Sin obligación de captura/declaración | Investigar infraestructura, configuración o defecto grave; no tratar como flujo normal. |

El uso de “excepción de ejecución” en conversación informal suele aludir a cualquier excepción observada durante la ejecución. No es sinónimo exacto de “no comprobada”: una `IOException` es comprobada aunque se lance durante la ejecución, mientras que `RuntimeException` es la rama definida por la jerarquía del lenguaje [55].

#### `try`, `catch`, `finally` y `try` con recursos

Un bloque `try` delimita las operaciones susceptibles de fallar. Los bloques `catch` se prueban en orden; una excepción puede capturarse por una clase compatible o por una superclase. Por eso, coloca los tipos específicos antes que los generales. El bloque `finally` se ejecuta al abandonar normalmente el `try` o un `catch`, y también durante una propagación ordinaria; no se debe confiar en él ante terminación forzada del proceso, caída de la JVM o del sistema [47] [151].

```java
try {
    int cantidad = Integer.parseInt(texto);
    System.out.println("Cantidad: " + cantidad);
} catch (NumberFormatException e) {
    System.err.println("La cantidad debe ser un entero: " + texto);
} finally {
    System.out.println("Fin del intento de conversión");
}
```

El código anterior captura un error de formato y permite continuar después del bloque. En una función de negocio, evita sustituir `System.err` por impresión directa si la aplicación tiene una capa de presentación o un sistema de registro; comunica el resultado con el mecanismo que corresponda a su contrato.

La forma de varios manejadores es `catch (TipoConcreto e)`. Java también permite **captura múltiple** cuando se aplica la misma reacción a excepciones no relacionadas por herencia:

```java
try {
    // Operación que puede producir IOException o SQLException.
} catch (IOException | java.sql.SQLException e) {
    // Una reacción común; e conserva un tipo compatible con ambas alternativas.
    throw new IllegalStateException("No se pudo completar la operación", e);
}
```

No incluyas simultáneamente en una captura múltiple un tipo y su subtipo, porque son alternativas redundantes. No uses `catch (Exception e)` para ocultar cualquier problema; mucho menos uses `catch (Throwable e)` salvo infraestructura muy especializada que vuelva a propagar los fallos graves.

`finally` es apropiado para acciones de limpieza que no cuenten con un mecanismo de gestión específico. No devuelvas valores ni ejecutes `return`, `break` o `continue` desde `finally`: ese control puede reemplazar una excepción o un valor de retorno originado en `try`/`catch` y hacer que el fallo original desaparezca. Para archivos, flujos, conexiones y otros objetos cerrables, prefiere `try` con recursos (*try-with-resources*), basado en `AutoCloseable` [47] [152].

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

class PrimeraLinea {
    static String leer(Path ruta) throws IOException {
        try (BufferedReader lector = Files.newBufferedReader(ruta)) {
            return lector.readLine();
        }
    }
}
```

Al abandonar el bloque, Java invoca automáticamente `close()`, tanto si la operación terminó normalmente como si lanzó una excepción. Si se declaran varios recursos, se cierran en orden inverso al de creación. Desde Java 9 también se puede usar en la cabecera una variable final o efectivamente final declarada previamente; la forma con declaración explícita dentro de `try (...)` es clara y compatible con versiones anteriores a ese cambio [152].

Si la operación principal lanza una excepción y el cierre también falla, se conserva como principal la excepción de la operación y la de cierre queda **suprimida**. Se puede inspeccionar con `getSuppressed()`. El siguiente ejemplo completo y ejecutable imprime el error principal y el error de cierre:

```java
import java.io.IOException;

public class DemoRecursos {
    static class Recurso implements AutoCloseable {
        @Override
        public void close() throws IOException {
            throw new IOException("fallo al cerrar");
        }
    }

    public static void main(String[] args) {
        try (Recurso recurso = new Recurso()) {
            System.out.println("operación principal");
            throw new IOException("fallo en la operación");
        } catch (IOException e) {
            System.out.println("principal: " + e.getMessage());
            for (Throwable suprimida : e.getSuppressed()) {
                System.out.println("suprimida: " + suprimida.getMessage());
            }
        }
    }
}
```

Ejecución:

```bash
javac DemoRecursos.java
java DemoRecursos
```

Salida esperada:

```text
operación principal
principal: fallo en la operación
suprimida: fallo al cerrar
```

Este ejemplo se compiló y ejecutó con OpenJDK 21.0.13.1. El cierre automático es importante porque la recolección de basura no reemplaza la liberación oportuna de descriptores de archivo, sockets y otros recursos del sistema operativo [56] [152].

#### `throw` y `throws`

`throw` lanza una instancia de `Throwable` en un punto concreto. `throws` aparece en la declaración de método o constructor e informa qué excepciones comprobadas pueden propagarse a quien lo llama. No son intercambiables: uno ejecuta el lanzamiento; el otro forma parte de la firma y del contrato de propagación [55] [47].

```java
static void validarSaldo(double saldo) {
    if (saldo < 0) {
        throw new IllegalArgumentException("El saldo no puede ser negativo");
    }
}

static String leerConfiguracion(Path ruta) throws IOException {
    return Files.readString(ruta);
}
```

La primera función rechaza un argumento inválido usando una excepción no comprobada; no necesita `throws`. La segunda permite que `IOException` se propague, así que lo declara. El llamador de `leerConfiguracion` debe capturarla o declararla también. Cuando se captura y se vuelve a lanzar una excepción, usa `throw e;` si sigue siendo apropiada. Si se traduce a una excepción de otra capa, conserva la causa: `throw new ConfiguracionException("No se pudo leer la configuración", e);`. La cadena causal aporta contexto sin perder el fallo original [56].

#### Excepciones personalizadas

Una excepción propia conviene cuando expresa una condición significativa del dominio y el código llamador puede reaccionar de manera distinta. Hereda de `Exception` para crear una comprobada o de `RuntimeException` para una no comprobada. No heredes directamente de `Throwable` ni de `Error` para errores de aplicación corrientes. Incluye mensaje claro y, cuando proceda, constructor que conserve la causa [55] [56].

```java
public class DemoExcepciones {
    static final class EdadInvalidaException extends Exception {
        private static final long serialVersionUID = 1L;

        EdadInvalidaException(String mensaje) {
            super(mensaje);
        }
    }

    static void validarEdad(int edad) throws EdadInvalidaException {
        if (edad < 0) {
            throw new EdadInvalidaException("La edad no puede ser negativa");
        }
    }

    public static void main(String[] args) {
        try {
            validarEdad(-1);
            System.out.println("Edad válida");
        } catch (EdadInvalidaException e) {
            System.out.println("Validación: " + e.getMessage());
        }
    }
}
```

Guárdalo como `DemoExcepciones.java` y ejecuta:

```bash
javac DemoExcepciones.java
java DemoExcepciones
```

Salida esperada:

```text
Validación: La edad no puede ser negativa
```

El ejemplo se compiló y ejecutó con OpenJDK 21.0.13.1. `validarEdad` declara la excepción comprobada; `main` decide capturarla. En una biblioteca o una jerarquía de excepciones serializables, `serialVersionUID` es una decisión explícita de compatibilidad; el identificador no cambia la lógica del lanzamiento.

Para una operación recuperable que el llamador razonablemente puede gestionar, una excepción comprobada puede documentar esa obligación. Para una precondición rota, un estado incompatible o un uso incorrecto de API suele ser más adecuado `IllegalArgumentException`, `IllegalStateException` u otra subclase de `RuntimeException`. No conviertas cada validación simple en una clase nueva ni emplees excepciones como sustituto de condiciones normales de control. El criterio es el contrato y la acción posible del llamador, no una regla universal sobre “checked” frente a “unchecked”.

#### Lectura de trazas de pila

Una **traza de pila** (*stack trace*) representa marcos de ejecución asociados a una excepción. Una instancia de `Throwable` puede contener mensaje, causa, traza y excepciones suprimidas. Cada línea `at ...` suele identificar clase, método, archivo y línea fuente; la primera entrada normalmente señala el lugar donde se creó o lanzó la excepción, seguida por los marcos que llegaron allí. Las causas se muestran en cadenas como `Caused by`; los cierres fallidos pueden aparecer como `Suppressed` [56].

Al investigar una traza:

1. Lee primero el tipo de excepción y su mensaje. Determina qué operación falló realmente.
2. Busca la primera línea que pertenezca a tu código, no asumas que la primera línea de toda la traza es el origen del defecto.
3. Recorre hacia arriba los llamadores para encontrar el límite donde debía tratarse o transformarse el fallo.
4. Inspecciona `Caused by` y `Suppressed`; una excepción envolvente puede ser útil para la capa actual, mientras la causa revela la operación subyacente.
5. Contrasta la línea con variables, datos de entrada y condiciones del entorno. Una traza es evidencia del recorrido, no una explicación automática de la causa raíz.

Ejemplo esquemático —el número de línea y el texto exacto dependen del código, compilador y ejecución—:

```text
java.lang.IllegalArgumentException: La edad debe ser un entero
    at ejemplo.Perfil.parsearEdad(Perfil.java:18)
    at ejemplo.Aplicacion.main(Aplicacion.java:7)
Caused by: java.lang.NumberFormatException: For input string: "doce"
    at java.base/java.lang.Integer.parseInt(Integer.java:...)
```

Si el compilador no incluyó metadatos de depuración, algunos nombres de archivo o números de línea pueden faltar. Al empaquetar o transformar bytecode, los números pueden corresponder a otra versión del código. No publiques trazas con datos personales, tokens, rutas sensibles o contenido secreto; las trazas y logs pueden filtrarse a sistemas de observabilidad o a usuarios. `printStackTrace()` escribe en `System.err` y es útil para ejercicios, pero en servicios debe preferirse un registro con contexto y control de acceso [56].

#### Depuración paso a paso

El depurador permite suspender una JVM, inspeccionar estado y avanzar de forma controlada. Un **punto de interrupción** (*breakpoint*) detiene el programa en una ubicación; un punto condicional solo se activa cuando una expresión es verdadera. Los controles comunes son avanzar sobre la siguiente línea (*step over*), entrar en una función (*step into*), salir de ella (*step out*) y continuar hasta otro punto. Observa valores antes y después de la operación sospechosa, la pila de llamadas y, en concurrencia, el hilo que ejecuta la línea. Los nombres de menús y teclas rápidas dependen de la versión del IDE y del sistema operativo.

**IntelliJ IDEA.** Abre la clase, haz clic en el margen junto a la línea para establecer un breakpoint y ejecuta la configuración con **Debug**. Al detenerse, examina variables y pila, añade *watches*, evalúa expresiones y usa los controles de avance. IDEA también permite breakpoints de excepción. La depuración requiere metadatos de depuración para mostrar plenamente variables y líneas; el compilador de Java de IDEA los genera por defecto en configuraciones habituales [153].

**Visual Studio Code.** Instala un JDK y las extensiones Java de Microsoft que incluyan depuración —en particular, *Debugger for Java*—. Abre el proyecto, fija un breakpoint y comienza con **F5** o la vista **Run and Debug**. Se puede depurar una clase, una prueba o una configuración de lanzamiento; proyectos con Maven/Gradle, módulos o parámetros especiales pueden requerir configuración adicional. La extensión de depuración es un componente externo a la JDK; su disponibilidad y compatibilidad dependen de las versiones instaladas [154].

**`jdb`.** El JDK incluye el depurador de consola `jdb`, útil cuando no hay IDE o al investigar un proceso JVM desde terminal. Compila con información de depuración (`-g`) y pon en marcha el depurador en vez de invocar `java` directamente [155]:

```bash
javac -g -d out src/ejemplo/Calculo.java
jdb -classpath out ejemplo.Calculo
```

En la consola interactiva de `jdb`, los comandos típicos son:

```text
stop at ejemplo.Calculo:12
run
locals
where
next
step
cont
quit
```

`stop at` establece un breakpoint por línea; `run` inicia la aplicación; `locals` muestra variables locales cuando hay información disponible; `where` muestra la pila; `next` avanza sin entrar en la llamada y `step` entra en ella. Para detenerse en una excepción concreta puede usarse `catch java.io.IOException`. La línea debe corresponder al archivo fuente y a una ubicación ejecutable; nombres de clases, rutas y separador de classpath pueden cambiar por paquete y sistema operativo. Al depurar en remoto, no expongas el puerto del protocolo JDWP a redes no confiables: cualquiera con acceso puede inspeccionar o controlar la JVM [155].

Un método repetible para un defecto lógico es crear una entrada mínima que lo reproduzca, formular el valor esperado, detenerse antes del cálculo, inspeccionar argumentos, recorrer una iteración y comparar el resultado real con el requisito. Evita cambiar muchas variables a la vez; confirma después la corrección con una prueba automatizada.

#### Registros de eventos (`logging`)

El *logging* conserva eventos durante una ejecución normal o anómala, con nivel, mensaje, contexto y, cuando es útil, la excepción completa. Sirve para diagnóstico posterior, operación y auditoría técnica; no sustituye al depurador ni a las pruebas. Registra transiciones relevantes y fallos con identificadores de operación, no cada detalle de cada variable. Evita contraseñas, tokens, datos personales y grandes cargas de usuario; aplica retención, controles de acceso y límites para no convertir los logs en otra fuente de riesgo.

#### `java.util.logging` (JUL)

`java.util.logging` es la API de registro incluida con Java, en el módulo `java.logging`. Ofrece `Logger`, niveles, manejadores (*handlers*), filtros y formateadores. No exige una dependencia de terceros, aunque su configuración y formato predeterminado pueden variar según el JDK, el archivo de propiedades y la aplicación [156].

```java
import java.util.logging.Level;
import java.util.logging.Logger;

public class DemoRegistro {
    private static final Logger LOG =
            Logger.getLogger(DemoRegistro.class.getName());

    public static void main(String[] args) {
        try {
            Integer.parseInt("x");
        } catch (NumberFormatException e) {
            LOG.log(Level.WARNING, "Entrada numérica inválida", e);
        }
    }
}
```

Compílalo con `javac DemoRegistro.java` y ejecútalo con `java DemoRegistro`. El ejemplo se ejecutó con OpenJDK 21.0.13.1. El programa registró un evento `WARNING`, el tipo `NumberFormatException` y su traza en la consola; fecha, formato, nombre de hilo y líneas exactas dependen de la configuración y plataforma. Los niveles de JUL incluyen `SEVERE`, `WARNING`, `INFO`, `CONFIG`, `FINE`, `FINER` y `FINEST`; la configuración determina cuáles se publican. `LOG.log(Level.WARNING, mensaje, e)` transmite la excepción al manejador para que la traza no se pierda.

#### SLF4J, Logback y Log4j

SLF4J es una **fachada** (*facade*), no un sistema de salida completo: el código llama a una API estable y una implementación o proveedor conectado en tiempo de ejecución decide dónde se escriben los eventos. **Logback** es una implementación que se integra con SLF4J. **Apache Log4j 2** ofrece una API y una implementación propias (`Log4j API` y `Log4j Core`), y puede conectarse con otros componentes. Los tres son proyectos externos, no partes de la biblioteca estándar del JDK [157] [158] [159].

| Opción | Qué es | Cuándo elegirla |
|---|---|---|
| JUL (`java.util.logging`) | API y mecanismos básicos del JDK. | Aplicación pequeña, dependencia cero o integración directa con registros del JDK. |
| SLF4J | Fachada de logging; necesita proveedor/backend para producir salida. | Biblioteca o aplicación que quiere desacoplar su código del backend. |
| Logback | Backend de terceros, con configuración y destinos de salida. | Aplicación que ya usa SLF4J y necesita un backend habitual de ese ecosistema. |
| Log4j 2 | API y backend de terceros con configuración y componentes amplios. | Aplicación que adopta explícitamente Log4j y requiere su conjunto de funciones. |

Ejemplo de llamadas con SLF4J:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class Servicio {
    private static final Logger LOG = LoggerFactory.getLogger(Servicio.class);

    public void procesar(String id) {
        LOG.info("Comienza el proceso {}", id);
        try {
            // Lógica de negocio.
        } catch (IllegalStateException e) {
            LOG.error("No se pudo procesar la solicitud {}", id, e);
            throw e;
        }
    }
}
```

Los marcadores `{}` permiten que la biblioteca formatee los argumentos según el nivel habilitado; el último argumento de tipo excepción se incorpora como traza. Para usar el ejemplo hay que declarar la API y exactamente un backend compatible en Maven/Gradle. SLF4J 2.0.20 y `logback-classic` son artefactos de terceros publicados en Maven Central; comprueba las versiones disponibles y sus requisitos de Java, fija versiones reproducibles y evita mezclar proveedores incompatibles [157] [158] [160] [161]. La documentación de los proyectos publica coordenadas y compatibilidad; no uses `LATEST` ni rangos dinámicos en una compilación de producción.

No agregues simultáneamente varios proveedores de SLF4J: la selección puede ser ambigua o generar avisos y comportamiento distinto del esperado. Si hay puentes entre JUL, SLF4J y Log4j, revisa la dirección de cada puente para evitar ciclos de redirección. Las bibliotecas reutilizables suelen emitir mediante una fachada y dejar que la aplicación configure el backend; la aplicación controla formato, destinos, niveles y políticas. Una llamada a log tampoco debe duplicar el mismo fallo en cada capa: registra donde se pueda añadir contexto útil y propaga o transforma sin perder la causa.

#### Niveles y contenido de un evento

Los nombres cambian entre sistemas, pero habitualmente se usan así:

- **TRACE / FINEST:** detalle muy granular para investigación puntual.
- **DEBUG / FINE:** diagnóstico de desarrollo o información técnica detallada.
- **INFO:** hitos normales de interés operacional.
- **WARN / WARNING:** condición inesperada que se pudo manejar o no impide continuar.
- **ERROR / SEVERE:** operación fallida que requiere atención.
- **FATAL:** disponible en algunas bibliotecas como Log4j; no es nivel estándar de SLF4J ni JUL.

El nivel exacto, la salida y el filtrado pertenecen al backend y su configuración. No registres la excepción en cada capa; evita tanto mensajes vagos (“falló”) como trazas sin contexto. Prefiere indicar qué operación se intentaba, un identificador no sensible y la excepción asociada. No construyas mensajes costosos de forma anticipada si el nivel está deshabilitado; usa parámetros o las APIs diferidas soportadas por la biblioteca.

#### Validación y tratamiento adecuado

Validar significa comprobar que los datos respetan las reglas antes de que afecten al estado del sistema. Para argumentos públicos, rechaza los inválidos cerca del límite de entrada y usa una excepción pertinente (`IllegalArgumentException` para un argumento ilegal es común); para errores esperables de I/O, captura o propaga `IOException`; para el dominio, define una excepción específica si el llamador necesita una respuesta diferente. La validación no sustituye al manejo de fallos ambientales: una ruta puede existir al validarla y desaparecer antes de abrirla, por ejemplo.

Al capturar, responde a una pregunta concreta: ¿puedo corregir, reintentar de forma limitada, proporcionar una alternativa, informar al usuario o convertir el error a un contrato más apropiado? Si la respuesta es no, propágalo. Si lo envuelves, conserva la causa. No retornes `null`, cero o una cadena vacía como si el resultado fuera válido salvo que esa sea la semántica documentada. Evita un `catch` vacío, un `catch (Exception)` que continúe como si nada hubiera ocurrido y mensajes sin información accionable.

Un reintento solo es correcto si la operación puede ser repetida sin duplicar efectos y existe una política acotada, normalmente con espera progresiva y límite de intentos. No reintentes indiscriminadamente errores de entrada o programación. No uses `assert` para validar datos externos de producción: las aserciones pueden desactivarse. Las invariantes internas y las comprobaciones de entrada externa tienen propósitos diferentes.

#### Errores frecuentes y correcciones

| Error frecuente | Consecuencia | Corrección |
|---|---|---|
| Capturar `Exception` o `Throwable` “por si acaso”. | Se ocultan fallos inesperados y se mezcla recuperación con errores graves. | Capturar el tipo más específico que la capa sabe manejar. |
| Capturar y no hacer nada. | Se pierde el fallo; el programa continúa con estado posiblemente inválido. | Resolver, registrar con contexto y propagar, o transformar conservando causa. |
| Capturar una excepción comprobada y devolver un valor ficticio. | El llamador interpreta un resultado erróneo como correcto. | Declarar la excepción o definir una alternativa explícita en el contrato. |
| Cerrar recursos solo al final del método. | Una excepción anterior puede dejar archivos, conexiones o bloqueos abiertos. | Usar `try` con recursos; reservar `finally` para recursos no compatibles. |
| Registrar y volver a lanzar en todos los niveles. | Una sola incidencia produce trazas duplicadas y ruido. | Registrar una vez en el límite donde se decide la respuesta. |
| Lanzar una excepción nueva sin la causa original. | La traza deja de mostrar el fallo inicial. | Pasar la causa al constructor de la excepción envolvente. |
| Usar excepciones para bifurcaciones normales. | Código difícil de seguir y con costo innecesario. | Usar condiciones o tipos de resultado cuando la situación es esperada. |
| Depurar sin reproducir ni comprobar entradas. | Se corrige el síntoma en vez de la causa. | Crear una reproducción mínima y añadir una prueba de regresión. |
| Registrar secretos o datos personales. | Exposición en archivos, servicios de observabilidad o alertas. | Minimizar, enmascarar y restringir los datos registrados. |

#### Recomendaciones de práctica profesional

1. Trata la excepción en la capa que tiene contexto suficiente para decidir qué hacer; de lo contrario, propágala con su tipo o causa intactos.
2. Haz los bloques `try` pequeños y enfocados. No abarques código ajeno a la operación cuyo fallo se quiere tratar.
3. Captura tipos específicos y ordena los `catch` desde los subtipos hacia los supertipos. Conserva una separación clara entre fallos de entrada, de dominio e infraestructura.
4. Para recursos que implementan `AutoCloseable`, usa `try` con recursos. Inspecciona excepciones suprimidas en diagnósticos cuando el cierre también pueda fallar.
5. Diseña excepciones personalizadas alrededor de contratos significativos. Proporciona mensajes accionables y encadena causas al traducir entre capas.
6. No conviertas `Error` en mecanismo de flujo. Investiga causas de `OutOfMemoryError`, `StackOverflowError` o `LinkageError` en su contexto de JVM, dependencias y entorno.
7. Combina pruebas, registros y depuración. Cada defecto corregido debe tener una prueba que detecte su reaparición cuando sea razonable.
8. Usa niveles de registro coherentes y evita tanto el exceso de mensajes como el silencio total. Centraliza la configuración en la aplicación, no en bibliotecas compartidas.
9. Mantén versiones de JDK, IDE, extensiones, bibliotecas y backend alineadas con el proyecto; las funciones del depurador y los formatos de logging no son idénticos entre proveedores, versiones y sistemas operativos.
10. Revisa la salida de error y los registros por contenido sensible, retención y acceso, además de su utilidad para diagnóstico.

#### Referencia rápida

| Necesidad | Forma Java |
|---|---|
| Lanzar excepción | `throw new IllegalArgumentException("mensaje");` |
| Declarar propagación comprobada | `String leer() throws IOException { ... }` |
| Capturar y manejar | `try { ... } catch (IOException e) { ... }` |
| Capturar alternativas independientes | `catch (IOException | SQLException e) { ... }` |
| Ejecutar acción final | `finally { ... }` |
| Cerrar recurso automáticamente | `try (BufferedReader lector = Files.newBufferedReader(ruta)) { ... }` |
| Conservar causa | `new MiExcepcion("contexto", causa)` |
| Consultar causa | `e.getCause()` |
| Consultar excepciones suprimidas | `e.getSuppressed()` |
| Imprimir traza durante diagnóstico | `e.printStackTrace()` —usar logging en aplicaciones— |
| Log de JUL con excepción | `logger.log(Level.WARNING, "contexto", e);` |
| Breakpoint de consola | `stop at paquete.Clase:línea` en `jdb` |

## 12. Seguridad en Java

Java ofrece comprobación de tipos, límites de arrays, APIs criptográficas, TLS y gestión automática de memoria, pero esas propiedades no vuelven segura automáticamente una aplicación. La seguridad depende de definir límites de confianza y aplicar el control adecuado al uso: validar datos, parametrizar SQL, codificar la salida web, autenticar, autorizar y limitar privilegios son defensas distintas [162] [163]. Este apartado se restringe al tema 12 de la guía base y a los controles indicados.

### 12.1 Validación de entradas

**Definición.** Validar es comprobar que un dato satisface el tipo, la forma, el rango y las reglas de negocio esperadas antes de utilizarlo. La validación debe aplicarse en el servidor en cada frontera de confianza: petición web, archivo, cola, servicio externo, base de datos heredada o configuración. La entrada válida sintácticamente puede ser semánticamente incorrecta; convertir una cadena a entero, por ejemplo, no demuestra que el valor esté dentro del rango aceptado [164].

**Cómo se aplica.** Define reglas específicas por campo y acepta solo lo que necesita la operación. Para un entero, limita primero su longitud, analiza con `Integer.parseInt`, y comprueba luego el intervalo. Para valores de un conjunto cerrado, usa una lista permitida. No intentes borrar caracteres “sospechosos” con una expresión regular universal: podrías alterar datos legítimos sin resolver SQL injection o XSS. La validación tampoco concede autorización: un ID bien formado no implica que el usuario pueda acceder al recurso [164].

```java
public final class Validacion {
    private Validacion() {}

    public static int cantidad(String texto) {
        if (texto == null || texto.length() > 6) {
            throw new IllegalArgumentException("Cantidad no válida");
        }
        final int valor;
        try {
            valor = Integer.parseInt(texto);
        } catch (NumberFormatException ex) {
            throw new IllegalArgumentException("La cantidad debe ser un entero", ex);
        }
        if (valor < 1 || valor > 10_000) {
            throw new IllegalArgumentException("Cantidad fuera de rango");
        }
        return valor;
    }

    public static void main(String[] args) {
        System.out.println(cantidad("24"));
    }
}
```

Guarda como `Validacion.java`, ejecuta `javac Validacion.java` y luego `java Validacion`. Salida esperada: `24`. Para una aplicación web, traduce el error a una respuesta de validación apropiada, sin exponer trazas ni detalles internos. Limita el tamaño de cuerpos antes de almacenarlos o analizarlos y establece límites de profundidad y elementos para estructuras anidadas [164].

**Errores frecuentes:** confiar solo en validación del navegador; aceptar entradas de “sistemas internos” sin validarlas; confundir parsing con autorización; permitir entradas enormes antes de validar; y usar una denylist de caracteres como defensa principal. Para nombres y texto libre, permite Unicode legítimo y limita longitud y formato según el propósito.

### 12.2 SQL parametrizado con JDBC

Una **inyección SQL** ocurre cuando datos externos se incorporan al texto de una consulta como si fueran parte de su sintaxis. En JDBC, `PreparedStatement` separa la estructura SQL de los valores y los transmite con métodos tipados como `setString` o `setLong` [165] [166].

```java
// INSEGURO: no usar. La entrada modifica la sintaxis SQL.
String sqlInseguro = "SELECT id FROM clientes WHERE correo = '" + correo + "'";
```

```java
// SEGURO para el valor: la entrada no se concatena a la consulta.
import javax.sql.DataSource;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public static boolean existeCliente(DataSource fuente, String correo)
        throws SQLException {
    String sql = "SELECT id FROM clientes WHERE correo = ?";
    try (Connection conexion = fuente.getConnection();
         PreparedStatement consulta = conexion.prepareStatement(sql)) {
        consulta.setString(1, correo);
        try (ResultSet resultados = consulta.executeQuery()) {
            return resultados.next();
        }
    }
}
```

`DataSource` representa una fuente de conexiones configurada por el entorno; el ejemplo no incorpora usuarios ni secretos de base de datos. El primer parámetro de JDBC se numera desde 1. Cierra conexión, consulta y resultados con `try`-with-resources; el pool de conexiones del `DataSource` normalmente gestiona la devolución de la conexión al pool al cerrarla. La consulta con `?` mantiene el texto fijo y `setString` liga el dato como valor [165].

Los parámetros solo sirven para **valores**, no para nombres de tabla, columna ni palabras como `ASC`/`DESC`. Si el usuario selecciona una columna de orden, mapea su elección a una cadena fija permitida en el código y rechaza cualquier alternativa. No reemplaces parámetros con escape manual. La parametrización no sustituye autorización, límites de privilegio de la cuenta SQL ni protección de procedimientos que construyan SQL dinámico [166]. Esto también aplica a JPQL/HQL: utilizar un ORM no protege automáticamente consultas concatenadas [167].

**Errores frecuentes:** crear un `PreparedStatement` después de concatenar la entrada; concatenar criterios de búsqueda o cláusulas `ORDER BY`; asumir que una entrada validada puede concatenarse; dar permisos de administrador a la cuenta de la aplicación; y registrar consultas con datos sensibles.

### 12.3 Codificación de salida web

**Codificar salida** significa representar los datos para que el parser de destino los trate como datos y no como marcado o código. No existe un escape universal: HTML, atributo HTML, JavaScript, CSS y URL tienen contextos distintos. La defensa debe aplicarse en el punto de salida y con el encoder apropiado; en una plantilla web, prefiere el autoescape documentado del framework [168].

```java
// INSEGURO en una respuesta HTML: el navegador interpreta el valor como marcado.
String htmlInseguro = "<p>" + nombreUsuario + "</p>";

// TERCERO: OWASP Java Encoder, para contenido de texto HTML.
import org.owasp.encoder.Encode;
String htmlSeguro = "<p>" + Encode.forHtmlContent(nombreUsuario) + "</p>";
```

`Encode.forHtmlContent` es para texto entre etiquetas HTML. Para un atributo HTML citado se requiere el encoder correspondiente, como `Encode.forHtmlAttribute`; no insertes datos no confiables en atributos de eventos (`onclick`), `<script>`, CSS o HTML interpretado. Para valores URL valida además el esquema y destino permitido, y codifica cada componente según corresponda. La codificación no limpia HTML si el producto pretende permitir contenido enriquecido: en ese caso hace falta un sanitizador mantenido con política explícita [168] [169].

OWASP Java Encoder es un proyecto de terceros. Su artefacto Maven Central es `org.owasp.encoder:encoder`; por ejemplo, la versión 1.6.0 estaba publicada al corte y requiere Java 8 o posterior [170]. En un proyecto Maven puede declararse así:

```xml
<dependency>
  <groupId>org.owasp.encoder</groupId>
  <artifactId>encoder</artifactId>
  <version>1.6.0</version>
</dependency>
```

Mantén el encoder actualizado y sigue su guía de contexto. No vuelvas a codificar los datos en capas posteriores sin necesidad, pues puede causar doble codificación o mostrar entidades literales.

### 12.4 Credenciales y almacenamiento de contraseñas

**No guardes contraseñas en texto plano ni cifradas para poder recuperarlas.** Para autenticación, almacena un hash de contraseña adaptativo: una derivación unidireccional, deliberadamente costosa y con sal aleatoria única. Hashes rápidos generales como `SHA-256(password)` no son apropiados: un atacante con la base puede probar candidatos a gran velocidad. OWASP recomienda Argon2id; bcrypt es alternativa compatible y extendida, con límite de entrada de 72 bytes que debe atenderse en sistemas que lo usen [171].

El JDK no incluye una API estándar de hashing de contraseñas con coste adaptativo apropiado para este uso. Puede usarse, por ejemplo, `spring-security-crypto` de Spring Security, biblioteca externa que proporciona `PasswordEncoder`, BCrypt y Argon2. La implementación Argon2 de Spring requiere Bouncy Castle disponible en el classpath [172]. Administra versiones por medio de un BOM o catálogo del proyecto y verifica las versiones vigentes antes de fijarlas; no copies una dependencia antigua de una guía.

```java
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;

// Selecciona el coste mediante mediciones en el entorno real.
PasswordEncoder codificador = new BCryptPasswordEncoder(12);
String hashParaGuardar = codificador.encode(passwordRecibida);

// En el inicio de sesión, compara con el hash almacenado;
// no calcules ni compares hashes mediante == o String.equals.
boolean coincide = codificador.matches(passwordPresentada, hashParaGuardar);
```

El valor devuelto es un hash con metadatos necesarios por la implementación; la biblioteca genera y guarda una sal individual. Guarda ese valor, nunca la contraseña recibida. La salida exacta cambia en cada registro por la sal aleatoria. No imprimas contraseña, hash ni token en logs. El coste `12` es solo un valor ilustrativo: mide el tiempo y consumo de memoria en el hardware y carga reales, equilibrando defensa y disponibilidad. Si eliges Argon2id con Spring, configura `Argon2PasswordEncoder` conforme a la versión documentada, comprueba la dependencia Bouncy Castle y mide sus parámetros. Los parámetros recomendados por OWASP pueden cambiar; aplica la hoja de almacenamiento vigente [171] [172].

**Contraseñas para servicios** (por ejemplo, una contraseña de base de datos) no son contraseñas de usuario para login. Si una aplicación debe recuperar ese secreto para autenticarse ante otro servicio, un hash no sirve: usa un gestor de secretos o servicio de identidad, restringe alcance, rota credenciales y evita código, repositorio, archivos de configuración públicos, argumentos de proceso y logs. Las variables de entorno reducen la exposición accidental frente a literales, pero no son por sí solas una bóveda ni protegen de procesos con acceso al entorno. Nunca inventes valores de credencial en ejemplos o commits.

### 12.5 Aleatoriedad segura y criptografía

`java.util.Random` es para simulación, no para claves, tokens de recuperación, identificadores de sesión o nonces impredecibles. `java.security.SecureRandom` proporciona un generador criptográficamente fuerte y se auto-siembra según el proveedor y la plataforma; no lo alimentes con una semilla predecible ni fijes manualmente la semilla en producción [173].

```java
import java.security.SecureRandom;
import java.util.Base64;

SecureRandom rng = new SecureRandom();
byte[] tokenBytes = new byte[32];
rng.nextBytes(tokenBytes);
String tokenUrl = Base64.getUrlEncoder().withoutPadding().encodeToString(tokenBytes);
System.out.println(tokenUrl.length());
```

La salida esperada es `43`; el contenido del token es aleatorio y, por eso, no se fija en la guía. Almacena tokens de un solo uso de forma segura, limita su vigencia y compara según el protocolo sin filtrarlos. `UUID.randomUUID()` puede servir para IDs, pero un identificador público no reemplaza un token secreto de autorización.

La arquitectura criptográfica Java (JCA/JCE) expone algoritmos a través de proveedores y APIs como `MessageDigest`, `Mac`, `Signature`, `Cipher`, `KeyStore` y `SecureRandom` [163]. Elige protocolos y transformaciones autenticadas mantenidas. No diseñes criptografía propia; evita algoritmos obsoletos, claves embebidas, modos ECB y cifrado sin autenticación. Para cifrado simétrico de datos, un patrón habitual es AES-GCM con nonce único por clave y etiqueta de autenticación; la clave requiere gestión, rotación y almacenamiento separado. Un nonce reutilizado con la misma clave puede comprometer confidencialidad e integridad. La API `Cipher` y su transformación dependen de los proveedores disponibles [174].

```java
import java.nio.charset.StandardCharsets;
import java.security.SecureRandom;
import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import javax.crypto.spec.GCMParameterSpec;

public class CifradoGcmDemo {
    public static void main(String[] args) throws Exception {
        KeyGenerator generador = KeyGenerator.getInstance("AES");
        generador.init(128);
        SecretKey clave = generador.generateKey(); // Solo para demo: se pierde al terminar.

        byte[] nonce = new byte[12];
        new SecureRandom().nextBytes(nonce);
        byte[] mensaje = "dato de demostración".getBytes(StandardCharsets.UTF_8);

        Cipher cifrador = Cipher.getInstance("AES/GCM/NoPadding");
        cifrador.init(Cipher.ENCRYPT_MODE, clave, new GCMParameterSpec(128, nonce));
        byte[] cifrado = cifrador.doFinal(mensaje);

        Cipher descifrador = Cipher.getInstance("AES/GCM/NoPadding");
        descifrador.init(Cipher.DECRYPT_MODE, clave, new GCMParameterSpec(128, nonce));
        String recuperado = new String(descifrador.doFinal(cifrado), StandardCharsets.UTF_8);
        System.out.println("Descifrado correcto: " + mensajeCorrecto(recuperado));
    }

    private static boolean mensajeCorrecto(String valor) {
        return "dato de demostración".equals(valor);
    }
}
```

Ejecución esperada con un JDK compatible: compilar `javac CifradoGcmDemo.java` y ejecutar `java CifradoGcmDemo`; salida: `Descifrado correcto: true`. **No es almacenamiento seguro listo para producción:** genera una clave efímera, no la persiste, no empaqueta el nonce con el ciphertext y no demuestra distribución, rotación ni respaldo. En una aplicación real conserva nonce y texto cifrado juntos, gestiona claves fuera del código y prueba la configuración del proveedor. Disponibilidad y restricciones criptográficas pueden variar por versión, proveedor del JDK y configuración del sistema.

### 12.6 TLS y comunicación de red

TLS aporta confidencialidad, integridad y autenticación del servidor si cliente, certificados y configuración se verifican correctamente. Usa HTTPS/TLS para tráfico sensible; OWASP recomienda TLS 1.3 y permitir TLS 1.2 solo cuando la compatibilidad lo requiera, y deshabilitar protocolos antiguos [175]. Las versiones predeterminadas habilitadas dependen del JDK, proveedor, propiedades, sistema operativo y configuración del servidor.

En Java, `java.net.http.HttpClient` (Java 11+) y JSSE usan configuración TLS del runtime por defecto cuando no se reemplaza el contexto SSL. Ejemplo de solicitud HTTPS con configuración estándar:

```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

HttpClient cliente = HttpClient.newHttpClient();
HttpRequest solicitud = HttpRequest.newBuilder(
        URI.create("https://api.example.test/estado"))
    .GET()
    .build();
HttpResponse<String> respuesta = cliente.send(
        solicitud, HttpResponse.BodyHandlers.ofString());
System.out.println(respuesta.statusCode());
```

Este ejemplo requiere un certificado válido para el host y confianza configurada en el runtime. El dominio `.test` es reservado para documentación: reemplázalo por el host real. No uses `TrustManager` que acepte todo, no desactives la comprobación del nombre del host, no ignores errores de certificado y no permitas HTTP para secretos en producción. En clientes servidor-a-servidor, configura truststore y, si procede, certificados cliente con administración de ciclo de vida. Las preferencias y algoritmos pueden estar afectados por las políticas del JDK/proveedor, el truststore y controles del sistema; prueba el despliegue real [163] [175].

### 12.7 Permisos y mínimo privilegio

El **principio de mínimo privilegio** limita cada proceso, servicio, cuenta de base de datos y archivo a lo necesario para su tarea. Java distingue accesibilidad de clases y miembros, módulos y permisos del sistema operativo; `private` o los módulos no sustituyen autorización de negocio ni protecciones del host. La guía de Oracle aconseja aislar componentes menos confiables y limitar privilegios mediante controles del sistema operativo, contenedores y separación de procesos [162].

No diseñes una solución nueva sobre `SecurityManager`: JEP 411 lo depreció para eliminación en Java 17 y JEP 486 lo deshabilitó permanentemente en JDK 24; esa función no debe tratarse como sandbox de código. JEP 486 declara que no se proporciona una sustitución equivalente para aislar código Java hostil [176]. Aísla código no confiable con procesos o contenedores restringidos, permisos de archivos y red, usuario de servicio dedicado, límites de CPU/memoria y controles del host. Configura las ACL de Windows o permisos POSIX de Linux/macOS según la plataforma. Evita ejecutar como administrador/root y entrega a la cuenta SQL únicamente permisos necesarios.

### 12.8 Serialización y deserialización

La serialización nativa de objetos Java (`ObjectInputStream`) puede activar métodos de clases durante la reconstrucción del grafo de objetos. Deserializar bytes de fuentes no confiables expone a ejecución de código o denegación de servicio, incluso cuando provienen de una base de datos o intermediario cuya integridad no está garantizada [162] [135].

**Recomendación principal:** no deserialices `ObjectInputStream` con datos no confiables. Prefiere formatos de datos como JSON con parser mantenido, límites de tamaño/profundidad y validación de esquema. Si la serialización Java es inevitable por compatibilidad, restringe clases permitidas y tamaño del grafo mediante filtros JEP 290, desde Java 9; por ejemplo, aplica un filtro específico por flujo antes de leer objetos [135]:

```java
ObjectInputFilter filtro = ObjectInputFilter.Config.createFilter(
    "maxdepth=8;maxrefs=500;maxbytes=1000000;maxarray=10000;" +
    "com.ejemplo.dto.*;!*");
entrada.setObjectInputFilter(filtro); // entrada es ObjectInputStream
```

El patrón solo permite las clases del paquete de DTO indicado y aplica límites; sustituye el paquete por clases estrictamente necesarias y prueba la compatibilidad. Los filtros no hacen segura por sí solos una clase permitida ni arreglan su lógica. No uses una allowlist amplia como `*`, no confíes en datos solo porque proceden de almacenamiento interno y no habilites filtrado global sin entender el impacto en todos los flujos. La disponibilidad exacta de filtros depende de la versión; JEP 290 se entregó en JDK 9 y JEP 415 añadió filtros contextuales en JDK 17 [135].

### 12.9 Dependencias y cadena de suministro

Cada biblioteca, plugin, wrapper y herramienta de construcción amplía la superficie de riesgo. Antes de incorporar una dependencia, revisa propósito, mantenimiento, historial de avisos, procedencia, licencias y transitivas. Fija versiones reproducibles mediante `pom.xml` y el mecanismo de versiones del proyecto; conserva inventario/SBOM, actualiza parches y analiza continuamente vulnerabilidades conocidas. OWASP recomienda controlar tanto bibliotecas como herramientas de compilación y pipeline, y verificar procedencia; los escáneres pueden producir falsos positivos y no certifican ausencia de vulnerabilidades [177].

Comandos de inspección Maven:

```bash
mvn -q dependency:tree
mvn -q help:effective-pom
```

Estos comandos muestran dependencias resueltas y configuración efectiva, no son un escaneo de seguridad. Complementa con un analizador SCA mantenido, por ejemplo OWASP Dependency-Check, política de actualización, revisión de plugins, repositorios confiables y análisis en CI. Evita rangos de versión amplios en producción, artefactos sin procedencia verificable y descargar jars desde sitios aleatorios. Maven Central ofrece metadatos de artefactos, pero una publicación en el repositorio no equivale a auditoría de seguridad del paquete [177].

### 12.10 Errores frecuentes y lista de revisión

Entre los errores más comunes están tratar Java como inmune a ataques por ser tipado; confundir validación con escaping; concatenar SQL en `Statement`; creer que un ORM evita cualquier inyección; renderizar entrada como HTML sin codificar; guardar contraseña, token o clave en texto claro; usar `Random` para secretos; desactivar validación TLS para “arreglar” certificados; deserializar objetos sin filtros; y ejecutar con permisos excesivos.

Antes de desplegar, comprueba que las entradas se validan según formato, rango y tamaño; que cada consulta liga sus parámetros y cualquier identificador dinámico procede de lista permitida; que salida web se codifica en el contexto exacto; que contraseñas se almacenan solo con hash adaptativo y salt, usando biblioteca mantenida; que secretos no aparecen en repositorios, logs o artefactos; que TLS valida certificado y host; que el proceso y la cuenta de BD tienen privilegios mínimos; que no se aceptan flujos Java serializados arbitrarios; y que las dependencias y herramientas se inventarían, analizan y actualizan. Revisa periódicamente las guías de Secure Coding de Oracle, la documentación del framework y OWASP, ya que versión, proveedor criptográfico, runtime y configuración del sistema cambian el comportamiento operativo [162] [163] [177] [174].

> Los ejemplos y salidas anteriores son ilustrativos y se presentan como código esperado; no se afirma que se hayan compilado o ejecutado en esta tarea. Antes de adoptar un ejemplo, valida compatibilidad con el JDK, driver JDBC, proveedor de seguridad, versión de dependencia y sistema operativo del proyecto.

## 13. Instalación, herramientas y ciclo de desarrollo

### Qué instalar: JDK, runtime, JRE y JVM

**JDK (Java Development Kit)** es el conjunto de desarrollo: incluye un runtime de Java y herramientas para compilar, empaquetar, documentar, depurar y diagnosticar programas. Entre sus comandos habituales están `java`, `javac`, `jshell`, `jar`, `javadoc` y `jdb`. Para escribir y compilar programas propios, instala un JDK, no solo un runtime [178] [179].

**Runtime** es el entorno que permite ejecutar una aplicación Java. **JVM (Java Virtual Machine)** es la máquina virtual que carga y ejecuta bytecode `.class`; no equivale a todo el runtime, que también incluye bibliotecas y componentes de plataforma. En versiones modernas, los proveedores distribuyen un JDK como la opción estándar para desarrollar y ejecutar. La antigua división “instalo JRE para ejecutar, JDK para programar” ya no describe todas las ofertas actuales: algunos proveedores aún ofrecen paquetes JRE, pero su composición y disponibilidad dependen del proveedor y de la versión. La documentación vigente de Oracle distingue Oracle JRE 8 de JDK 11 y posteriores, y su FAQ no presenta un JRE general actual independiente para desarrolladores; una imagen runtime a medida puede construirse con `jlink` [11] [180] [179].

El código fuente `.java` se compila normalmente a bytecode `.class` con `javac`; después, `java` inicia la JVM y lanza la clase o aplicación. El bytecode puede ejecutarse en sistemas diferentes si existe un runtime compatible, pero la compatibilidad depende de la versión de class file, las APIs usadas, los módulos, las bibliotecas externas y el sistema anfitrión. La alternativa `java Archivo.java` compila y ejecuta un programa de un solo archivo en modo fuente; resulta práctica para ejemplos y utilidades pequeñas, pero no sustituye una compilación/build reproducible de un proyecto [181] [182].

### Versiones: GA, LTS y actualización

Al corte de esta guía, **JDK 27** es la versión de características más reciente que alcanzó disponibilidad general (GA) el **15 de septiembre de 2026**. OpenJDK muestra JDK 28 en desarrollo. La última LTS es **Java 25**, publicada el 16 de septiembre de 2025; Oracle la designa LTS y OpenJDK indica que será LTS para la mayoría de los proveedores. La etiqueta LTS no impone una duración universal: periodo de mantenimiento, binarios, soporte comercial y fechas finales son decisiones de cada proveedor [18] [132] [183].

No se debe confundir la versión de características GA con su última actualización. Oracle publicó **JDK 27.0.1.1 el 17 de noviembre de 2026**; esa es la actualización de JDK 27 que aparece en las notas oficiales al corte. La versión concreta ofrecida por Temurin u otro proveedor puede tener otra numeración o calendario de publicación; comprueba la página de releases y el soporte de la combinación de sistema operativo y arquitectura antes de fijarla en producción [57].

Para aprender o iniciar un sistema nuevo con un horizonte estable, Java 25 LTS es una elección razonable si los frameworks y las dependencias la soportan. Para probar características recientes o validar compatibilidad hacia adelante, instala Java 27 en paralelo. En un proyecto real, fija y documenta la versión que exige el equipo o el despliegue. Evita depender accidentalmente de “la Java que encuentre primero `PATH`”.

#### OpenJDK, Oracle JDK y Eclipse Temurin

**OpenJDK** es el proyecto comunitario de desarrollo de las implementaciones de referencia de Java SE. No es una marca única de producto: distintas organizaciones construyen y distribuyen binarios basados en el código OpenJDK, con combinaciones de plataforma, calendarios de actualizaciones, parches, servicios y soporte diferentes. Las fuentes de OpenJDK se distribuyen bajo GPLv2 con Classpath Exception (y excepciones adicionales aplicables a componentes/ensamblado) [18] [184].

**Oracle JDK** es la distribución de Oracle. No confundas Oracle JDK con los binarios “Oracle OpenJDK”: Oracle distribuye ambos, pero pueden diferir en licencia, actualizaciones y soporte. Para JDK 25 y posteriores, Oracle declara que Oracle JDK está disponible bajo **Oracle No-Fee Terms and Conditions (NFTC)**, que permite uso gratuito incluso comercial y de producción, sujeto al texto de la licencia. El roadmap anuncia que las actualizaciones de Oracle JDK 25 posteriores a septiembre de 2028 están previstas bajo OTN; esa fecha futura es un plan sujeto a las condiciones publicadas, no una promesa de que toda versión de Oracle Java será siempre gratuita. Las ramas Oracle JDK 8, 11, 17 y 21 tienen condiciones distintas según la versión exacta de actualización; algunas actualizaciones recientes se ofrecen solo a clientes Oracle o para usos limitados bajo OTN. Lee la licencia aplicable al artefacto y a la actualización descargada antes de redistribuirla o usarla comercialmente [3] [185].

**Eclipse Temurin** es la distribución de binarios OpenJDK del proyecto Eclipse Adoptium. Adoptium publica builds multiplataforma sometidas a pruebas de compatibilidad Java SE TCK; sus páginas indican que el código OpenJDK está bajo GPLv2 con Classpath Exception, mientras que scripts e infraestructura de build tienen licencias propias. TCK-compliant no significa que cada binario sea idéntico a otro proveedor, ni que incluya soporte comercial específico. Verifica soporte de plataforma, política de actualizaciones, licencias de componentes, acuerdos de soporte y cadena de suministro de la distribución elegida [186].

**Regla práctica:** selecciona proveedor y versión con base en la política de actualizaciones y soporte requerida; conserva el aviso de licencia junto con el inventario de dependencias. Evita instaladores reempaquetados de sitios de descargas no oficiales. Descarga desde el proveedor o usa gestores de paquetes con origen y firma verificables.

### Instalación en Windows, macOS y Linux

Los pasos siguientes usan Temurin 25 LTS como base reproducible. La nomenclatura de paquetes permite seleccionar otra versión disponible, por ejemplo Temurin 27. La disponibilidad puede variar por arquitectura, distribución y fecha. Comprueba los instaladores, checksums y plataformas soportadas en Adoptium antes de instalar [186] [187]. También es válido descargar Oracle JDK desde Oracle o usar un JDK de la distribución Linux, teniendo en cuenta la licencia y la antigüedad de los paquetes.

#### Windows

En la página oficial de Temurin descarga el `.msi` que corresponda a Windows y la arquitectura del equipo. En el instalador gráfico, activa las opciones para añadir el JDK a `PATH` y definir `JAVA_HOME` si las necesitas. La documentación del MSI señala que el instalador está pensado para instalación por máquina y que las funciones ofrecidas pueden incluir esas dos opciones; la compatibilidad de MSI publicada allí depende de arquitectura [187]. Otra alternativa confiable es `winget`, si el paquete aparece en el catálogo de tu sistema:

```powershell
winget install EclipseAdoptium.Temurin.25.JDK
```

Para usar la versión GA más reciente, selecciona el paquete/instalador Temurin 27 disponible en su página oficial; no asumas que un alias “LTS” instala la GA. Abre una terminal nueva y comprueba:

```powershell
java --version
javac --version
where.exe java
$env:JAVA_HOME
```

`where.exe java` muestra los ejecutables encontrados en `PATH`; el primero normalmente es el que ejecuta la shell. Para probar una configuración solo en la ventana actual de PowerShell, sustituye la ruta por el directorio real del JDK:

```powershell
$env:JAVA_HOME = 'C:\Program Files\Eclipse Adoptium\jdk-25.0.x.x-hotspot'
$env:Path = "$env:JAVA_HOME\bin;$env:Path"
```

No copies literalmente el nombre de carpeta del ejemplo: cambia entre versiones y builds. Para persistirlo, abre **Editar las variables de entorno del sistema**, crea `JAVA_HOME` apuntando a la raíz del JDK —no a `bin`— y añade `%JAVA_HOME%\bin` a `Path`. Cierra y vuelve a abrir terminales/IDE tras cambiarlo. Evita `setx PATH ...` sin revisar el valor existente: puede truncar o alterar el PATH del usuario.

#### macOS

Descarga desde Adoptium el paquete `.pkg` apropiado para Apple silicon o Intel y para la versión deseada, y sigue el instalador. También es posible instalar el paquete desde Terminal con `installer -pkg archivo.pkg -target /`; requiere privilegios de administrador. Temurin instala bajo `/Library/Java/JavaVirtualMachines/` según su guía. La instalación del JDK normalmente permite seleccionar el JDK con las herramientas de macOS sin modificar manualmente el PATH [188].

Comprueba la instalación y descubre el JDK 25:

```bash
java --version
javac --version
/usr/libexec/java_home -V
/usr/libexec/java_home -v 25
```

Para la sesión actual de `zsh`, si está instalado Java 25:

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 25)
export PATH="$JAVA_HOME/bin:$PATH"
```

Para Java 27, cambia `-v 25` por `-v 27` y confirma que esté instalado. Para que la selección persista, coloca las líneas apropiadas en `~/.zshrc` y abre una nueva Terminal. Si utilizas Bash, el archivo de inicio puede ser `~/.bash_profile` o `~/.bashrc`, según cómo se inicie la shell.

#### Linux

Puedes instalar el JDK desde el repositorio de tu distribución o desde los repositorios oficiales de Adoptium. La versión de una distribución puede ir por detrás de GA, pero suele integrarse con sus herramientas de actualización. En Debian/Ubuntu, una vez configurado el repositorio firmado de Adoptium siguiendo sus instrucciones oficiales:

```bash
sudo apt update
sudo apt install temurin-25-jdk
```

Para Fedora/RHEL/CentOS, configura el repositorio RPM de Adoptium según la distribución y luego instala:

```bash
sudo dnf install temurin-25-jdk
```

El paquete `temurin-27-jdk` puede usarse si el repositorio lo publica para tu distribución y arquitectura. En Debian/Ubuntu las instrucciones oficiales requieren importar la clave GPG de Adoptium y añadir el repositorio; en RPM hay que habilitar el repositorio con comprobación GPG. No agregues una URL de repositorio ni una clave tomada de una fuente no confiable [189].

Valida qué ejecutables se resuelven y qué JDK está activo:

```bash
java --version
javac --version
command -v java
command -v javac
printf '%s\n' "$JAVA_HOME"
```

Si la distribución no establece `JAVA_HOME`, identifica la raíz real del JDK instalada. Para una configuración temporal de Bash/Zsh, reemplaza la ruta por la que corresponda a tu sistema:

```bash
export JAVA_HOME=/ruta/real/al/jdk-25
export PATH="$JAVA_HOME/bin:$PATH"
```

Coloca esas líneas en `~/.bashrc`, `~/.zshrc` o el archivo de inicio propio de tu shell para hacerlas persistentes. En servidores o agentes CI, prefiere la configuración declarativa del servicio y una ruta/versionado explícitos en lugar de depender del perfil interactivo de un usuario.

#### `PATH` y `JAVA_HOME`: qué significan

`PATH` es la lista de directorios donde la shell busca comandos como `java` y `javac`. `JAVA_HOME` es una convención utilizada por herramientas —por ejemplo Maven o Gradle— para identificar la raíz de un JDK. No es una variable requerida por la JVM ni una función que instale Java. En la configuración habitual, `JAVA_HOME` apunta a la carpeta raíz del JDK y `PATH` incluye su subdirectorio `bin`. `PATH` puede contener varios JDK; el orden determina cuál comando encuentra primero la shell [190] [191].

Un diagnóstico rápido compara variables, versiones y rutas. Si `java --version` y `javac --version` muestran versiones principales distintas, probablemente hay más de un JDK instalado o el PATH no coincide con `JAVA_HOME`. Los IDE y las herramientas de build pueden escoger un runtime distinto al de la terminal, así que revisa también la configuración del proyecto.

### Herramientas básicas del JDK

| Comando | Propósito | Ejemplo |
|---|---|---|
| `java` | Ejecuta una clase, JAR, módulo o fuente Java. | `java -cp out HolaJava` |
| `javac` | Compila fuente Java en archivos `.class`. | `javac -d out src/HolaJava.java` |
| `jshell` | Consola interactiva (REPL) para probar expresiones, declaraciones y métodos. | `jshell` |
| `jar` | Crea, inspecciona y manipula archivos JAR. | `jar --create --file app.jar -C out .` |
| `javadoc` | Genera documentación HTML a partir de comentarios Javadoc. | `javadoc -d docs src/*.java` |
| `jdb` | Depurador de línea de comandos. | `jdb -classpath out HolaJava` |
| `jlink` | Construye una imagen runtime personalizada con módulos seleccionados. | Se usa al preparar una distribución autocontenida. |

La documentación de JDK 26 enumera estas herramientas y explica sus opciones; las opciones exactas pueden variar con la versión. Para ver la ayuda instalada usa, por ejemplo, `javac --help`, `java --help` o `jshell --help` [181] [182] [179].

#### `java`, `javac` y `jshell`

El flujo compilado convencional consiste en compilar fuentes con `javac` y ejecutar la clase compilada con `java`. Para el programa sin paquete `HolaJava`, `java` recibe el nombre de clase, no el nombre del archivo `.class`: `java -cp out HolaJava`. `-cp`/`--class-path` especifica dónde buscar clases y dependencias; los separadores son `:` en macOS/Linux y `;` en Windows. Para proyectos mayores, deja classpath y compilación al gestor de build [181] [182].

La opción `--release N` de `javac` compila contra la versión de lenguaje y APIs Java SE disponibles para esa versión. Por ejemplo, desde JDK 27, `javac --release 25 ...` permite fijar Java 25 como destino si el código y las dependencias son compatibles. No uses solo `-source`/`-target` como sustituto sin entender el riesgo de compilar accidentalmente contra APIs nuevas. El uso de funciones **preview** requiere habilitarlas explícitamente tanto al compilar (`--enable-preview --release N`) como al ejecutar (`--enable-preview`), y está sujeto a cambios entre versiones; no es una base estable de producción. Características **incubator** también se identifican explícitamente en sus JEP/módulos y no deben tratarse como API estándar estable [182] [144].

`jshell` abre un REPL (read-eval-print loop): escribe una expresión, declaración o método y recibe evaluación inmediata. Por ejemplo:

```text
$ jshell
jshell> 2 + 3
$1 ==> 5
jshell> String saludo = "Hola"
saludo ==> "Hola"
jshell> /exit
```

El formato de prompts e identificadores de resultados puede variar. JShell es adecuado para explorar una API o probar una idea, pero no organiza por sí mismo el código en módulos, pruebas y dependencias de un producto. Dentro de la sesión, `/help`, `/list` y `/exit` son comandos de JShell; no son sentencias Java [192].

### Primer programa: editar, compilar y ejecutar

Crea un directorio vacío con esta estructura:

```text
hola-java/
└── src/
    └── HolaJava.java
```

Guarda en `src/HolaJava.java`:

```java
public class HolaJava {
    public static void main(String[] args) {
        String nombre = args.length > 0 ? args[0] : "Java";
        System.out.println("¡Hola, " + nombre + "!");
    }
}
```

`HolaJava` es una clase pública, por lo que el archivo se llama `HolaJava.java`. `main` es el punto de entrada convencional que utiliza el lanzador para arrancar esta forma de aplicación. El programa toma el primer argumento de línea de comandos si existe; de lo contrario, usa `Java`. `System.out.println` escribe una línea en la salida estándar. Esta forma clásica de `main` es estable y compatible con las versiones de referencia [193].

Desde la raíz `hola-java`, compila en un directorio de salida separado y ejecuta:

```bash
javac -d out src/HolaJava.java
java -cp out HolaJava
java -cp out HolaJava Ada
```

Salida esperada:

```text
¡Hola, Java!
¡Hola, Ada!
```

`-d out` guarda las clases generadas en `out` y evita mezclar `.class` con las fuentes. La primera invocación ejecuta sin argumentos; la segunda pasa `Ada` a `main`. La compilación exitosa normalmente no imprime nada. Para fijar compatibilidad con Java 25 desde un JDK más nuevo, compila con `javac --release 25 -d out src/HolaJava.java` y ejecuta con un runtime Java 25 o posterior compatible.

Para un único archivo didáctico, también se puede ejecutar sin dejar clases compiladas en el directorio:

```bash
java src/HolaJava.java Ada
```

Este modo fuente lo compila temporalmente y ejecuta la clase principal; resulta cómodo para pruebas pequeñas, no aporta por sí solo empaquetado, gestión de dependencias ni un ciclo de build completo [181].

### IDE, editor y depurador

Un **IDE (Integrated Development Environment)** integra edición, navegación, compilación, pruebas y depuración. IntelliJ IDEA, Eclipse IDE for Java Developers y Visual Studio Code con las extensiones Java son opciones habituales. VS Code es un editor extensible: para soporte Java instala el paquete/extensiones oficiales recomendados y configura un JDK. Los IDE pueden tener un runtime propio para ejecutarse, pero eso no reemplaza el JDK del proyecto. Configura en cada proyecto el SDK/JDK objetivo; el IDE puede usar otro JDK que el `PATH` del sistema [194] [178].

El depurador permite colocar breakpoints, avanzar paso a paso, inspeccionar variables y pila de llamadas, y evaluar expresiones. Aprende a reproducir el fallo con una compilación limpia y a comprobar qué versión de Java usa tanto el IDE como el build. Los atajos y pantallas cambian entre IDEs y versiones.

### Maven, Gradle y dependencias

Java no trae un gestor universal de paquetes integrado en el lenguaje. **Maven** y **Gradle** son herramientas de build: compilan, ejecutan pruebas, gestionan dependencias, generan artefactos y pueden integrarse con CI. Maven describe el proyecto en `pom.xml`; Gradle utiliza `build.gradle` o `build.gradle.kts`. Ambos pueden descargar bibliotecas desde repositorios como **Maven Central**, que es un repositorio público de artefactos, no un gestor ni una garantía automática de seguridad. Revisa versión, proveedor, licencia y mantenimiento de cada dependencia [190] [191].

Para Maven, la instalación global requiere un JDK y que `JAVA_HOME` o `PATH` apunten correctamente. Al corte, la página oficial de instalación identifica Maven 3.10.0 como estable y exige JDK 8 o posterior; las exigencias de la versión que instales pueden cambiar [190]. Comandos habituales:

```bash
mvn --version
mvn test
mvn package
```

Si el repositorio trae `mvnw` y `.mvn/wrapper/`, utiliza el **Maven Wrapper** (`./mvnw test` en macOS/Linux o `mvnw.cmd test` en Windows) para que el proyecto seleccione su versión de Maven. Las dependencias y la versión de Java se declaran en el POM; no instales librerías copiando JARs al directorio del sistema.

Gradle también requiere un JDK para ejecutarse. La documentación consultada para Gradle 9.8.2 establece JDK 17 o superior para ejecutar Gradle; la compatibilidad para compilar o ejecutar código Java puede tener una matriz diferente, por lo que se consulta la tabla oficial antes de actualizar [191]. Si el proyecto incluye `gradlew` o `gradlew.bat`, usa el **Gradle Wrapper** en lugar de instalar Gradle por separado:

```bash
./gradlew --version
./gradlew test
./gradlew build
```

En Windows:

```powershell
.\gradlew.bat --version
.\gradlew.bat test
.\gradlew.bat build
```

El Wrapper fija la distribución usada por el proyecto y hace más reproducibles las builds; conserva y revisa sus archivos de configuración. Para un proyecto nuevo, utiliza el mecanismo de inicialización documentado por la versión de Gradle elegida y confirma el JDK requerido por los plugins.

### Ciclo profesional de desarrollo

Un ciclo mantenible separa el código fuente, artefactos generados y dependencias:

1. **Definir plataforma:** decidir vendor y versión de JDK, por ejemplo Java 25 LTS, y documentar versión mínima y objetivo de compilación.
2. **Crear el proyecto:** comenzar con estructura y build reproducibles; versionar código y archivos Maven/Gradle, no directorios de salida ni cachés locales.
3. **Editar:** escribir código en el IDE/editor con formato coherente y avisos del compilador.
4. **Compilar/build:** ejecutar `javac` para ejemplos sencillos o `./mvnw package` / `./gradlew build` en proyectos gestionados. Usar `--release` o la configuración equivalente del build para fijar las APIs destino.
5. **Probar y depurar:** ejecutar pruebas, reproducir defectos, usar debugger y examinar trazas. No considerar “compila” como sinónimo de “está correcto”.
6. **Revisar dependencias:** bloquear versiones mediante archivos de build/lock cuando proceda; evaluar origen, licencia, avisos de seguridad y actualizaciones.
7. **Empaquetar y desplegar:** producir JAR u otro artefacto; comprobarlo en un entorno equivalente al destino y mantener actualizado el runtime. Si se necesita una aplicación autocontenida, evaluar `jlink`/`jpackage` y la licencia/redistribución del runtime elegido.

Para compilar proyectos antiguos, no cambies el JDK de desarrollo a ciegas: registra la versión, prueba dependencias y plugins y actualiza en rama controlada. En CI y equipos, acuerda una versión exacta de proveedor/update o automatiza la gestión de JDK; los números `25` y `27` por sí solos no identifican todos los parches.

### Errores frecuentes y diagnóstico

**`'java' no se reconoce` / `command not found`:** Java no está instalado o el directorio `bin` no está en `PATH`. Abre una terminal nueva y consulta la ruta de instalación; verifica primero `PATH` y luego `JAVA_HOME`.

**`javac` no se reconoce, pero `java` sí:** probablemente hay solo un runtime disponible en `PATH`, o `java` y `javac` pertenecen a instalaciones distintas. Instala un JDK y revisa `where.exe java` en Windows o `command -v java; command -v javac` en macOS/Linux.

**`Could not find or load main class`:** se ha pasado un nombre de clase incorrecto, el directorio actual/classpath no contiene los `.class`, o el nombre cualificado no coincide con el paquete. Ejecuta desde la raíz adecuada y usa, por ejemplo, `java -cp out paquete.HolaJava` para una clase en `package paquete;`.

**`class file has wrong version` / `UnsupportedClassVersionError`:** se intenta ejecutar bytecode compilado por una versión más nueva que la JVM activa. Actualiza el runtime de destino o recompila con `--release` apropiado y verifica que el IDE/servicio usa el mismo JDK.

**Maven/Gradle detecta otro Java:** estas herramientas pueden seleccionar JDK a través de `JAVA_HOME`, `PATH`, configuración del IDE o ajustes del Wrapper. Consulta `mvn --version`, `gradle --version` o `./gradlew --version` para saber qué JVM inició el build; corrige la selección ahí, no solo en el código.

**Versiones desalineadas:** `java --version`, `javac --version` y el JDK del IDE difieren. No elimines instalaciones al azar: cambia la selección del proyecto y orden de PATH de forma explícita, comprueba los comandos y reinicia la terminal/IDE.

**El gestor de paquetes instala una versión anterior:** los repositorios de OS pueden actualizarse a un ritmo distinto a Oracle/OpenJDK/Adoptium. Consulta `java --version`, confirma la fuente del paquete y usa el repositorio oficial del proveedor si es necesario una versión concreta; no descargues binarios de sitios agregadores desconocidos.

## 14. Pruebas de software

JUnit 6 es la generación actual de JUnit a esta fecha. Conserva los nombres históricos de módulos: **JUnit Platform** descubre y ejecuta motores de prueba; **JUnit Jupiter** proporciona el modelo moderno para escribir pruebas; **JUnit Vintage** permite ejecutar temporalmente pruebas JUnit 3/4 desde la plataforma y está obsoleto para nuevas pruebas. Por tanto, la anotación habitual sigue siendo `org.junit.jupiter.api.Test`, no un paquete llamado `junit6` [102].

### Qué prueban los tests

Una prueba automatizada ejecuta código con entradas controladas y compara el comportamiento observado con un resultado o contrato esperado. Las pruebas ayudan a detectar regresiones y a documentar decisiones; no demuestran que el programa esté libre de defectos. Conviene probar resultados, efectos relevantes y límites de los contratos, no repetir en la prueba cada línea de implementación.

Una **prueba unitaria** examina una unidad pequeña —por ejemplo, un método o clase— con pocas dependencias y retroalimentación rápida. Una **prueba de integración** comprueba que componentes reales colaboran correctamente: servicio y base de datos, serializador y formato, o cliente y servidor. Una **prueba funcional** verifica un requisito observable del sistema desde la perspectiva de una función o flujo de usuario. Puede recorrer varias capas y ejecutarse mediante una interfaz web, API o CLI. Estas categorías describen el propósito y alcance, no anotaciones especiales de JUnit; el proyecto decide cómo separarlas y ejecutarlas.

JUnit sirve para tests unitarios y también puede organizar pruebas de integración o funcionales. La diferencia no es que JUnit cambie de API, sino qué partes reales se ponen a prueba, cuánto dura la ejecución y qué servicios externos se necesitan. Conviene mantener pruebas pequeñas y numerosas para reglas locales, y reservar las pruebas amplias para verificar contratos de colaboración y flujos críticos.

### Primer test con JUnit Jupiter

Una prueba normalmente contiene preparación, acción y comprobación. Esta organización suele denominarse **Arrange–Act–Assert**: prepara los datos, llama a la unidad y compara el resultado. El nombre del método debe describir el comportamiento esperado, por ejemplo, `aplicaDescuentoDelDiezPorCiento`.

La clase de producción del ejemplo recibe y devuelve centavos enteros. Define que el precio final se redondea hacia abajo al centavo más cercano; el uso de `long` en el cálculo intermedio evita desbordamiento en la multiplicación para los valores `int` válidos.

```java
// src/main/java/ejemplo/Descuento.java
package ejemplo;

public final class Descuento {
    public int aplicar(int subtotalCentimos, int porcentaje) {
        if (subtotalCentimos < 0) {
            throw new IllegalArgumentException("El subtotal no puede ser negativo");
        }
        if (porcentaje < 0 || porcentaje > 100) {
            throw new IllegalArgumentException("El porcentaje debe estar entre 0 y 100");
        }
        return (int) ((long) subtotalCentimos * (100 - porcentaje) / 100);
    }
}
```

El test comprueba varios resultados con datos parametrizados y también dos límites inválidos:

```java
// src/test/java/ejemplo/DescuentoTest.java
package ejemplo;

import static org.junit.jupiter.api.Assertions.assertEquals;
import static org.junit.jupiter.api.Assertions.assertThrows;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.CsvSource;

class DescuentoTest {
    private Descuento descuento;

    @BeforeEach
    void crearSujetoDePrueba() {
        descuento = new Descuento();
    }

    @ParameterizedTest
    @CsvSource({
        "10000, 10, 9000",
        "5000,   0, 5000",
        "99,    50,   49"
    })
    void calculaElPrecioFinalEnCentimos(int subtotal, int porcentaje, int esperado) {
        assertEquals(esperado, descuento.aplicar(subtotal, porcentaje));
    }

    @Test
    void rechazaSubtotalNegativo() {
        assertThrows(IllegalArgumentException.class,
                () -> descuento.aplicar(-1, 10));
    }

    @Test
    void rechazaPorcentajeSuperiorAlCien() {
        assertThrows(IllegalArgumentException.class,
                () -> descuento.aplicar(1000, 101));
    }
}
```

`@Test` identifica un test convencional. `@ParameterizedTest` ejecuta el mismo contrato con argumentos diferentes; `@CsvSource` provee filas de valores, convertidas a los tipos de los parámetros. `assertEquals(esperado, real)` compara el resultado. `assertThrows` verifica que una acción lance el tipo de excepción esperado y falla si no se lanza o se lanza otra. Las pruebas parametrizadas reducen duplicación cuando las filas expresan casos del mismo comportamiento; cada invocación aparece individualmente en los reportes [195] [196] [197].

`@BeforeEach` se ejecuta antes de cada test y crea una instancia independiente del objeto bajo prueba. También existen `@AfterEach`, `@BeforeAll` y `@AfterAll`. Por defecto, JUnit crea una instancia de la clase de prueba por método; los métodos `@BeforeAll` y `@AfterAll` deben ser `static`, excepto cuando se elige explícitamente el ciclo `PER_CLASS` con `@TestInstance`. Usa los callbacks para preparar y cerrar recursos necesarios, no para esconder la lógica central del test [195].

Las assertions más habituales incluyen `assertTrue`, `assertFalse`, `assertNull`, `assertNotNull`, `assertSame`, `assertIterableEquals`, `assertAll` y `assertDoesNotThrow`. `assertAll` ejecuta un grupo de comprobaciones y reporta fallos conjuntamente. Los mensajes de fallo pueden agregarse como último argumento; cuando construirlos es costoso, se puede pasar un `Supplier<String>` para evaluarlos solo si hay fallo. No confundas `Assertions.assertTrue(...)` de JUnit con la palabra clave `assert` del lenguaje Java: las aserciones nativas de Java pueden estar desactivadas en ejecución si no se habilitan con `-ea`, por lo que no sustituyen al framework de tests [196] [198].

#### Salida esperada

Con la configuración Maven de más abajo, la ejecución debería reportar cinco invocaciones exitosas: tres filas parametrizadas y dos tests convencionales. El formato exacto y el tiempo varían según la versión de Surefire, JDK, sistema operativo y configuración.

```text
Tests run: 5, Failures: 0, Errors: 0, Skipped: 0
BUILD SUCCESS
```

Esta salida de JUnit es **ilustrativa, no una ejecución verificada**. En el entorno de elaboración había OpenJDK 21, pero no estaban instalados Maven ni Gradle; no se compiló ni ejecutó la suite JUnit. Sí se compiló la clase `Descuento` con `javac` y se comprobó manualmente que los cinco casos de producción mostraran `9000`, `5000`, `49` y rechazaran las dos entradas inválidas. La salida real del runner puede tener diferencias de formato.

### Tipos de prueba y selección de dependencias

#### Unitarias

Aíslan una regla de negocio o unidad lógica, con entradas simples y sin depender de red, bases de datos reales o el reloj del sistema. Son apropiadas para validar cálculos, decisiones, conversión de datos y manejo de errores. Mantén las colaboraciones reales cuando sean rápidas y deterministas; un mock no mejora automáticamente una prueba.

#### De integración

Verifican la colaboración entre piezas concretas. Si la integración implica una base de datos, usa una base de prueba o instancia efímera compatible con el motor real y limpia los datos. Si depende de una API externa, no hagas llamadas a producción desde cada ejecución rutinaria: usa un entorno controlado, un servidor simulado cuando sea suficiente, o pruebas de contrato. Separa estas pruebas de las unitarias si requieren recursos lentos o variables.

Maven Surefire suele ejecutar clases `*Test.java`. Maven Failsafe se usa habitualmente para pruebas de integración, con clases como `*IT.java`; `mvn verify` ejecuta las fases de integración y verificación cuando Failsafe está configurado. En Gradle puede crearse una tarea o source set de integración separado; la documentación del plugin JVM Test Suite aún marca algunas APIs de configuración de test suites como incubating, por lo que hay que consultar el estado de la versión Gradle usada [199] [200] [201].

#### Funcionales

Validan un flujo o capacidad frente a un requisito observable, como crear un pedido mediante la API y comprobar la respuesta, o ejecutar una CLI y revisar su salida y código de estado. Según el producto, pueden usar JUnit junto con un cliente HTTP, servidor de pruebas o framework adicional. Las pruebas funcionales deben comprobar lo que el usuario o consumidor puede observar; inspeccionar detalles internos los vuelve frágiles ante refactorizaciones.

### Mockito: mocks y stubs

Mockito es una biblioteca **de terceros**, no parte de Java ni de JUnit. Un **stub** proporciona una respuesta predefinida a una llamada. Un **mock** permite además verificar interacciones relevantes con una dependencia. Mockito 5 requiere Java 11 como mínimo y ofrece una extensión para integrarse con Jupiter; el proyecto Mockito publica artefactos versionados independientemente de JUnit [202] [203].

Usa mocks cuando una dependencia externa sea costosa, no determinista o difícil de preparar, y cuando el contrato incluya una interacción importante. No simules cada llamada ni objetos de valor sencillos. Si una prueba queda excesivamente acoplada al orden interno de llamadas, puede romperse al refactorizar aun cuando el comportamiento observable no haya cambiado.

Ejemplo ilustrativo de prueba de una regla que consulta inventario. `Inventario` y `PedidoService` son clases del proyecto, que se incluirían en `src/main/java`:

```java
interface Inventario {
    boolean hayUnidades(String sku, int cantidad);
}

final class PedidoService {
    private final Inventario inventario;

    PedidoService(Inventario inventario) {
        this.inventario = inventario;
    }

    boolean puedeCrearPedido(String sku, int cantidad) {
        return inventario.hayUnidades(sku, cantidad);
    }
}
```

```java
@ExtendWith(MockitoExtension.class)
class PedidoServiceTest {
    @Mock
    Inventario inventario;

    @Test
    void devuelveSiHayExistenciasParaLaCantidadSolicitada() {
        when(inventario.hayUnidades("LIBRO-7", 2)).thenReturn(true);
        var servicio = new PedidoService(inventario);

        assertTrue(servicio.puedeCrearPedido("LIBRO-7", 2));
        verify(inventario).hayUnidades("LIBRO-7", 2);
    }
}
```

El test requiere estos imports estáticos y de Mockito/JUnit: `org.junit.jupiter.api.Test`, `org.junit.jupiter.api.extension.ExtendWith`, `org.mockito.Mock`, `org.mockito.junit.jupiter.MockitoExtension`, además de `org.mockito.Mockito.when`, `org.mockito.Mockito.verify` y `org.junit.jupiter.api.Assertions.assertTrue`. Una versión publicada verificable del artefacto Jupiter es 5.23.0; añádela con alcance `test` en Maven:

```xml
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-junit-jupiter</artifactId>
    <version>5.23.0</version>
    <scope>test</scope>
</dependency>
```

En Gradle, declárala como `testImplementation 'org.mockito:mockito-junit-jupiter:5.23.0'`. Comprueba el repositorio Maven Central al actualizar, ya que Mockito cambia independientemente de la versión de JUnit [202] [203].

### Configuración y comandos Maven

La ubicación convencional es `src/main/java` para producción y `src/test/java` para pruebas. Un proyecto pequeño puede usar esta estructura:

```text
proyecto/
├── pom.xml
└── src/
    ├── main/java/ejemplo/Descuento.java
    └── test/java/ejemplo/DescuentoTest.java
```

Configuración mínima con JUnit 6.1.3 y Surefire 3.6.1. El `release` de Java fija el nivel del lenguaje y las APIs usadas al compilar; JUnit 6, en cualquier caso, requiere un JDK de al menos 17 para ejecutar el motor [102] [199] [200].

```xml
<properties>
    <maven.compiler.release>17</maven.compiler.release>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <junit.version>6.1.3</junit.version>
</properties>

<dependencies>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter</artifactId>
        <version>${junit.version}</version>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>org.junit.platform</groupId>
        <artifactId>junit-platform-launcher</artifactId>
        <version>${junit.version}</version>
        <scope>test</scope>
    </dependency>
</dependencies>

<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.14.1</version>
        </plugin>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>3.6.1</version>
        </plugin>
    </plugins>
</build>
```

Desde la raíz del proyecto:

```bash
mvn test
mvn -Dtest=DescuentoTest test
mvn clean verify
```

`mvn test` compila producción y tests y ejecuta los tests unitarios detectados. La opción `-Dtest=...` selecciona una clase para Surefire. `clean` elimina resultados previos; `verify` alcanza la fase de verificación del ciclo Maven, lo que resulta útil cuando se incorporan plugins de cobertura o Failsafe. En Windows puede usarse `mvnw.cmd` si el proyecto incluye Maven Wrapper; en Linux/macOS, `./mvnw`. Surefire 3.6.1 ya utiliza la plataforma JUnit para ejecutar frameworks compatibles; al integrar una versión anterior, comprueba sus requisitos y configuración [199] [200].

Para ejecutar también clases `*IT`, añade Failsafe al `pom.xml` y ejecuta `mvn verify`:

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-failsafe-plugin</artifactId>
    <version>3.6.1</version>
    <executions>
        <execution>
            <goals>
                <goal>integration-test</goal>
                <goal>verify</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

Failsafe separa la fase de ejecución de integración de la decisión final de build, de modo que puede completar la fase de verificación y mostrar los resultados. Usa nombres convencionales `*IT` para evitar que Surefire y Failsafe ejecuten el mismo test por duplicado [199] [200].

### Configuración y comandos Gradle

El plugin Java crea una tarea `test` y un source set de pruebas. Para JUnit Platform se debe activar `useJUnitPlatform()`. Ejemplo en Groovy DSL (`build.gradle`):

```groovy
plugins {
    id 'java'
}

repositories {
    mavenCentral()
}

dependencies {
    testImplementation platform('org.junit:junit-bom:6.1.3')
    testImplementation 'org.junit.jupiter:junit-jupiter'
    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'
}

tasks.named('test') {
    useJUnitPlatform()
}
```

La BOM (Bill of Materials) alinea las versiones de los artefactos JUnit. Gradle también puede configurarse con Kotlin DSL (`build.gradle.kts`); no mezcles sintaxis Groovy en ese archivo. Comandos habituales:

```bash
./gradlew test
./gradlew test --tests 'ejemplo.DescuentoTest'
./gradlew clean test
```

En Windows usa `gradlew.bat` con los mismos argumentos. Gradle genera por defecto resultados y reportes HTML de pruebas bajo `build/reports/tests/test/`. El uso de `./gradlew` o `gradlew.bat` emplea la versión declarada por el wrapper del proyecto, que no necesariamente coincide con la más reciente instalada globalmente [199] [201].

### Cobertura con JaCoCo

JaCoCo es una herramienta externa de análisis de cobertura para Java, no un componente del JDK ni de JUnit. Instrumenta bytecode durante las pruebas y puede generar métricas de instrucciones, ramas, líneas, métodos y clases. La cobertura indica qué parte del código fue recorrida en esas ejecuciones; no mide directamente si las expectativas son adecuadas, si los resultados son correctos ni si se han cubierto todos los requisitos. La cobertura de ramas de JaCoCo considera bifurcaciones de `if` y `switch`, pero no cuenta los caminos de manejo de excepciones como ramas [204] [205].

Al corte, la versión estable consultada es JaCoCo 0.8.16; declara soporte oficial de archivos de clase Java 27. No uses una versión anterior sin comprobar compatibilidad, sobre todo si compilas con el último JDK [206]. Añade al bloque `<plugins>` del POM:

```xml
<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.16</version>
    <executions>
        <execution>
            <goals>
                <goal>prepare-agent</goal>
            </goals>
        </execution>
        <execution>
            <id>reporte-cobertura</id>
            <phase>verify</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

Ejecuta `mvn clean verify`. El informe HTML se genera normalmente en `target/site/jacoco/index.html`. JaCoCo requiere que el proceso de tests se lance con el agente; por ejemplo, Surefire no debe configurarse sin fork (`forkCount=0`) si se espera que el agente recopile cobertura. En proyectos con módulos, pruebas de integración o requisitos de umbral, consulta los goals `report-aggregate`, `report-integration` y `check`; una cobertura mínima es una política del proyecto, no una cifra universal [204].

En Gradle puede activarse el plugin integrado de JaCoCo:

```groovy
plugins {
    id 'java'
    id 'jacoco'
}

jacoco {
    toolVersion = '0.8.16'
}

tasks.named('test') {
    useJUnitPlatform()
}
```

Ejecuta `./gradlew clean test jacocoTestReport`. La tarea produce normalmente el informe HTML en `build/reports/jacoco/test/html/index.html`. El plugin Gradle configura el agente e informa resultados; verifica en la documentación de tu versión de Gradle la compatibilidad y tareas disponibles [201] [206].

No persigas un porcentaje alto mediante tests que solo ejecutan líneas sin comprobar comportamiento. Atiende primero las reglas con impacto, rutas de error, límites de entrada y decisiones de negocio. Un informe parcial puede ser legítimo si el código excluido es generado, de integración no ejecutada o no relevante, pero documenta el motivo y evita excluirlo solo para mejorar el porcentaje.

### Evitar pruebas frágiles

Una prueba es frágil cuando falla por variaciones irrelevantes o por detalles internos, en vez de señalar un cambio de comportamiento importante. Para reducirlo:

- Comprueba resultados públicos y contratos. Evita verificar llamadas internas que no forman parte del requisito.
- No dependas del orden de ejecución entre métodos. Cada test debe preparar su estado y poder ejecutarse de forma aislada.
- Evita `Thread.sleep()` para sincronizar pruebas concurrentes; utiliza mecanismos de coordinación o esperas con condición y timeout acotado.
- No dependas de servicios de red, credenciales personales, rutas absolutas, zona horaria o idioma del equipo. Usa recursos temporales y datos de prueba controlados.
- En pruebas de fechas, inyecta `Clock` o un proveedor de tiempo cuando la lógica depende del instante actual.
- En pruebas de colecciones, compara contenido/orden solo si el contrato garantiza ese orden.
- Evita tests aleatorios no reproducibles; fija la semilla cuando el azar sea parte del caso y registra la semilla al fallar.
- Usa timeouts para detectar bloqueos, no para exigir duraciones exactas que varían con la carga del host.
- Mantén mocks mínimos; stubbing innecesario puede ocultar cambios en el diseño y acoplar el test a la implementación.
- Haz que los tests sean deterministas y seguros para ejecución paralela antes de habilitar paralelismo.

### Errores frecuentes y buenas prácticas

**El comando termina con `BUILD SUCCESS`, pero no ejecutó tests.** Revisa la convención de nombres, la ruta `src/test/java`, la anotación `@Test`, la dependencia del motor Jupiter y la compatibilidad de Surefire/Gradle. Un build exitoso sin tests descubiertos no demuestra que el código esté probado.

**Usar `assert` nativo como si fuera JUnit.** `assert condicion;` es una sentencia Java cuyo chequeo puede desactivarse si la JVM no se inicia con `-ea`. Para tests automatizados usa assertions de JUnit, que reportan el fallo al runner [196] [198].

**Probar solo el caso feliz.** Añade valores límite y entradas inválidas conforme al contrato. En el ejemplo del descuento se comprueba subtotal negativo y porcentaje fuera del rango, además de tres cálculos válidos.

**Comparar valores de punto flotante con igualdad exacta.** Los tipos `float` y `double` representan aproximaciones binarias. En cálculos decimales como precios usa unidades enteras o `BigDecimal` con política de redondeo explícita; si se prueban magnitudes flotantes, define tolerancia adecuada.

**Compartir estado mutable entre tests.** Evita campos estáticos mutables, orden fijo y datos persistentes compartidos. Limpia recursos en callbacks o mediante recursos temporales; los tests deben poder repetirse.

**Confundir cobertura con calidad.** 100 % de líneas ejecutadas no significa que las salidas se validaron ni que todos los requisitos se cubrieron. Revisa asserts, casos de borde, ramas y los fallos que el test detectaría [205].

**Sobrecargar pruebas unitarias con mocks.** Si el comportamiento depende de que un adaptador real traduzca correctamente SQL o HTTP, un test que simula ese adaptador no comprueba esa integración. Combina tests unitarios rápidos con pruebas controladas del adaptador real.

Como regla profesional, automatiza la suite en cada cambio, separa pruebas rápidas de las que requieren servicios externos, fija versiones de herramientas y dependencias, y reporta fallos con contexto útil. Usa JDKs y sistemas operativos representativos de los destinos reales cuando existan dependencias de plataforma. Las APIs mostradas de Java no son preview ni incubator; JUnit, Mockito y JaCoCo son dependencias de terceros, con versiones y requisitos propios. Las features preview del JDK requieren habilitación expresa y no se usan en estos ejemplos.

## 15. Ecosistema y bibliotecas

Los ejemplos de Java SE en esta sección usan APIs estables y evitan depender de características preview o incubator. Los comandos y salidas son ilustrativos de una instalación compatible: no se afirma que se hayan ejecutado en esta tarea. La versión del JDK, el proveedor, el sistema operativo, la arquitectura y la configuración local pueden cambiar tanto los comandos disponibles como la salida exacta.

### Qué abarca el ecosistema Java

**Definición:** el ecosistema Java comprende el lenguaje y las especificaciones de Java SE, las implementaciones de la máquina virtual (JVM) y del JDK, sus bibliotecas, herramientas, sistemas de construcción, repositorios de componentes, frameworks, IDE, prácticas de distribución y comunidades. El término “Java” no designa un único instalador ni un único proveedor: el mismo programa puede compilarse con un JDK y ejecutarse en otra implementación compatible, siempre que respete las versiones de bytecode, APIs, dependencias y plataforma que la aplicación requiere.

Conviene distinguir tres capas. **Java SE** es la plataforma estándar de propósito general y sus APIs especificadas. El **JDK** es el kit de desarrollo que contiene el compilador, el lanzador y herramientas adicionales; algunas APIs `jdk.*` son propias del JDK y no están garantizadas en todas las implementaciones Java SE. Las **bibliotecas y frameworks externos** se distribuyen por separado y tienen sus propias versiones, requisitos, licencias, políticas de mantenimiento y compatibilidad [94].

#### Biblioteca estándar de Java SE

La biblioteca estándar reúne APIs mantenidas dentro de la especificación Java SE. El módulo fundacional `java.base` contiene tipos de uso transversal, incluidos `java.lang`, `java.util`, `java.io`, `java.nio`, `java.time`, `java.math` y partes de seguridad. Otros módulos estándar añaden, por ejemplo, HTTP y WebSocket (`java.net.http`), SQL/JDBC (`java.sql`), procesamiento XML (`java.xml`), escritorio (`java.desktop`), logging (`java.logging`) y gestión (`java.management`) [94].

Estas APIs son el primer recurso que conviene conocer antes de añadir una dependencia externa. En particular, las colecciones, flujos, fechas, rutas y operaciones de entrada/salida suelen resolver muchos problemas comunes sin incorporar paquetes ajenos. La biblioteca estándar también mantiene contratos de API entre versiones Java SE, aunque una API puede deprecarse o cambiar según las reglas de compatibilidad y el ciclo del JDK.

**Ejemplos representativos:**

- `java.util`: colecciones (`List`, `Map`, `Set`), comparadores, `Optional`, utilidades y `ServiceLoader`.
- `java.util.stream`: operaciones de transformación y reducción sobre datos; no es una biblioteca para cada problema de procesamiento ni reemplaza automáticamente un diseño eficiente.
- `java.time`: fechas, horas, zonas horarias e intervalos temporales; suele ser preferible a las APIs heredadas de fechas para código nuevo.
- `java.nio.file`: rutas y archivos mediante `Path`, `Files` y proveedores del sistema de archivos.
- `java.net.http`: cliente HTTP y WebSocket incluido en la plataforma desde Java 11.
- `java.sql`: API JDBC para acceder a bases de datos; el controlador concreto de cada motor suele ser una dependencia externa.
- `java.xml`: APIs Java de procesamiento XML; su disponibilidad no implica que se incluya una biblioteca general para leer JSON o CSV.
- `java.logging`: logging estándar sencillo; muchas aplicaciones eligen una fachada o backend externo según sus requisitos.

La plataforma no incorpora una API estándar general de JSON. Para JSON suelen usarse bibliotecas externas como Jackson, Gson o JSON-B; para CSV, Apache Commons CSV u OpenCSV; para persistencia de objetos, bibliotecas o frameworks como Hibernate ORM. Son ejemplos del ecosistema, no componentes de Java SE ni recomendaciones oficiales de Oracle. Evalúa soporte de la versión elegida, licencia, seguridad, mantenimiento, tamaño de dependencias y necesidades del proyecto antes de adoptarlos.

La API estándar de Java SE no debe confundirse con la totalidad de las clases incluidas en cualquier JDK. La documentación separa módulos `java.*`, que definen las APIs Java SE, de módulos `jdk.*`, que son específicos del JDK y no necesariamente portables a otras implementaciones. Por ejemplo, APIs y herramientas como `jdk.jfr`, `jdk.jpackage`, `jdk.jlink`, `jdk.jshell` o `jdk.incubator.vector` pertenecen al universo JDK, pero no deben tratarse como APIs generales de Java SE sin revisar su estado y alcance [94].

#### Ejemplo: resolver primero con la biblioteca estándar

Este programa solo usa Java SE. Guarda el archivo como `Resumen.java`:

```java
import java.time.LocalDate;
import java.util.List;

public class Resumen {
    public static void main(String[] args) {
        List<String> tareas = List.of("compilar", "probar", "documentar");
        System.out.println("Fecha: " + LocalDate.of(2026, 11, 18));
        System.out.println("Tareas: " + String.join(", ", tareas));
    }
}
```

Compilación y ejecución en Linux/macOS o PowerShell, con un JDK configurado en `PATH`:

```shell
javac Resumen.java
java Resumen
```

Salida esperada:

```text
Fecha: 2026-11-18
Tareas: compilar, probar, documentar
```

`List.of` crea una lista no modificable, `LocalDate` representa una fecha civil sin zona horaria y `String.join` une texto. No se necesita descargar bibliotecas ni abrir una conexión de red. Si el requisito fuese representar una hora de una zona concreta, habría que utilizar un tipo con zona, como `ZonedDateTime`, no asumir que `LocalDate` incluye hora o zona.

**Errores frecuentes:** usar una biblioteca externa para algo ya cubierto con una API estándar; asumir que todos los tipos de una biblioteca marcada `jdk.*` forman parte de cualquier runtime Java; elegir una API heredada sin revisar alternativas actuales; no revisar las notas de migración cuando se cambia de versión mayor; tratar valores de fecha local como marcas temporales universales.

**Buenas prácticas:** leer el JavaDoc de la versión objetivo, elegir la API pública más específica y mantenida, declarar explícitamente formatos y zonas temporales y aislar el código externo detrás de interfaces cuando el acoplamiento o el cambio probable lo justifique. No crear una capa de abstracción sin necesidad: la biblioteca estándar puede ser suficiente.

### Herramientas del JDK

El **JDK** contiene herramientas para crear, inspeccionar, documentar, empaquetar, diagnosticar y ejecutar programas Java. Las herramientas más habituales incluyen `javac` (compilador), `java` (lanzador de aplicaciones), `jshell` (REPL interactivo), `jar` (archivos JAR), `javadoc` (documentación), `jdeps` (dependencias), `jlink` (imágenes de runtime modulares), `jpackage` (paquetes de aplicación) y herramientas de monitorización como `jcmd`, `jfr` y `jconsole`. Algunas herramientas tienen limitaciones por plataforma o están disponibles solo en ciertas distribuciones/instalaciones JDK; el manual de la versión instalada es la referencia para opciones exactas [94] [207].

Comprueba qué binarios está invocando la terminal:

```shell
java --version
javac --version
jshell --version
```

La salida varía entre actualizaciones, proveedores, sistemas y arquitecturas. Una forma abreviada de salida podría ser:

```text
openjdk 27.0.1 ...
javac 27.0.1
```

Si `java` existe y `javac` no, probablemente hay solo un runtime o el `PATH` apunta a otra instalación; para compilar se requiere un JDK. Comprueba además la ruta del ejecutable (`where java` en Windows; `command -v java` en shells Unix) y, en proyectos Maven, `mvn --version`, porque el proceso de construcción podría estar usando otro JDK que el IDE o la terminal.

El JDK ofrece documentación versionada para APIs, herramientas, especificaciones, funciones nuevas y cambios incompatibles. Para JDK 27, consulta la API, las guías y las especificaciones de la misma versión; no mezcles por descuido la documentación de otra versión [94]. `jshell` es útil para explorar expresiones pequeñas, pero no sustituye a un proyecto con compilación, pruebas y dependencias declaradas.

### Bibliotecas externas y Maven Central

Una **biblioteca externa** es código publicado fuera de Java SE/JDK que una aplicación incorpora para ofrecer una capacidad adicional: serialización JSON, un driver JDBC, un cliente de nube, validación o una API de pruebas. Un **repositorio de artefactos** almacena los archivos publicados y sus metadatos. Maven Central es un repositorio público central del ecosistema JVM; Sonatype mantiene su portal de búsqueda y documentación. Que un paquete esté disponible allí significa que puede resolverse desde ese repositorio, no que Oracle, Apache Maven o Sonatype certifiquen que sea seguro, apropiado, mantenido o “oficial” para Java [208] [209].

Los componentes se identifican comúnmente mediante coordenadas `groupId:artifactId:version` (GAV), por ejemplo `org.junit.jupiter:junit-jupiter:5.12.2`. El `groupId` identifica el espacio del proyecto, `artifactId` el componente y `version` una publicación concreta. Una dependencia directa es la que el propio código solicita; una transitiva llega a través de otra dependencia. Maven resuelve el grafo y ofrece ámbitos como `compile`, `runtime`, `provided` y `test`; Gradle ofrece configuraciones equivalentes con su propio modelo. En proyectos de producción, registra versiones revisadas y resuelve versiones transitivas de forma consciente; evita rangos flotantes o “la última” sin reproducibilidad [208] [209].

Ejemplo de una declaración Maven de dependencia de prueba, sin que implique que sea necesaria en una aplicación concreta:

```xml
<dependencies>
  <dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter</artifactId>
    <version>5.12.2</version>
    <scope>test</scope>
  </dependency>
</dependencies>
```

El fragmento especifica una versión y un alcance; no es un proyecto Maven completo. El número es una versión ilustrativa fijada para mostrar sintaxis, no una recomendación de versión vigente al momento de ejecutar este ejemplo. Para escoger una versión real, comprueba el proyecto oficial, Central, la matriz de compatibilidad del framework, las alertas de seguridad y los requisitos de Java. En proyectos con muchas dependencias relacionadas, un **BOM** (*Bill of Materials*) puede centralizar versiones compatibles; se importa según la documentación de la plataforma o framework y no debe combinarse indiscriminadamente con BOM de ecosistemas distintos.

**Recomendaciones de cadena de suministro:** utiliza dependencias necesarias y explícitas; fija versiones (y plugins de construcción) revisadas; inspecciona el árbol de dependencias; consulta licencia y política de mantenimiento; actualiza parches de seguridad; verifica sumas o firmas cuando el proceso de distribución lo requiera; y no publiques credenciales de repositorios en archivos versionados. Los análisis automatizados ayudan, pero no demuestran ausencia de vulnerabilidades ni sustituyen la revisión de procedencia y uso.

### Gestores de dependencias y construcción: Maven y Gradle

**Maven** y **Gradle** no son bibliotecas ni frameworks de aplicación. Son herramientas de construcción y gestión de dependencias que automatizan la compilación, las pruebas, el empaquetado y otros pasos del ciclo. Maven describe el proyecto de forma declarativa en `pom.xml` y organiza tareas por ciclos/fases; Gradle usa un modelo de tareas y plugins, con scripts Groovy (`build.gradle`) o Kotlin (`build.gradle.kts`). Los dos pueden resolver artefactos de Maven Central y repositorios adicionales, compilar Java y cooperar con frameworks. La elección depende del proyecto, del equipo y de los plugins: no hay una regla universal de que uno sea siempre más rápido o mejor.

El **Maven Wrapper** (`mvnw`, `mvnw.cmd`) y el **Gradle Wrapper** (`gradlew`, `gradlew.bat`) seleccionan la versión de la herramienta definida por el repositorio, lo que reduce diferencias entre equipos y CI. Usa el wrapper comprobado por el proyecto en vez de depender de una instalación global no fijada. No confundas tres versiones: el JDK con que se ejecuta Maven/Gradle, el JDK que compila el código y el nivel de Java al que se dirige el bytecode. Toolchains y opciones de compilación permiten seleccionarlos por separado, aunque cada versión del gestor y sus plugins tiene sus propias capacidades.

Apache Maven 3.10.0 es una versión GA estable de la serie 3 y requiere JDK 8 o posterior; Apache Maven 4.0.0-rc-7 seguía siendo candidata de versión, no GA, en el registro oficial consultado al corte. Por tanto, no debe describirse una versión RC como versión estable. El equipo Apache mantiene las dos últimas series GA según su historial. Gradle publica una matriz por versión: en la documentación vigente al corte, el Gradle más nuevo referido allí admite ejecutar Gradle sobre JVM 17–27, mientras algunas versiones anteriores requieren JDK más antiguo. “Puede compilar para Java X” y “puede ejecutarse sobre JDK X” no son el mismo soporte [210] [211].

Ejemplo de tareas comunes para un proyecto existente que incluya los wrappers:

```shell
./mvnw test
./mvnw package
./mvnw dependency:tree
```

En Windows usa `mvnw.cmd` en lugar de `./mvnw`. En Gradle:

```shell
./gradlew test
./gradlew build
./gradlew dependencies
```

Las tareas, fases, salida e incluso el nombre de cada tarea pueden depender de los plugins configurados. No ejecutes esos comandos fuera de un proyecto correspondiente ni asumas que su resultado será idéntico en todas las versiones.

**Errores frecuentes:** compilar con una versión y desplegar en una JVM más antigua que no entiende el formato de bytecode; configurar `source`/`target` sin asegurar que se compila contra las APIs del nivel objetivo; editar la versión del wrapper de forma no revisada; copiar plugins o BOM de otro proyecto sin verificar compatibilidad; asumir que la versión elegida por una dependencia transitiva es la deseada; incluir en el artefacto final dependencias marcadas solo para prueba.

**Buena práctica:** declara de manera explícita el nivel objetivo (`--release` con `javac` o su equivalente del plugin), configura toolchains cuando el equipo trabaje con JDK distintos, usa wrappers versionados, fija plugins y dependencias, y verifica el artefacto con pruebas en la JVM real de despliegue.

### Frameworks: categorías y opciones

Un **framework** ofrece estructura, convenciones y componentes para resolver una categoría de aplicaciones. A menudo controla parte del ciclo de vida y llama al código de la aplicación (inversión de control), mientras una biblioteca suele ser invocada directamente. Framework no significa estándar Java ni está incluido en el JDK. Spring, Quarkus y Micronaut son proyectos de terceros; Jakarta EE es un conjunto de especificaciones administradas por la Eclipse Foundation y se implementa en productos compatibles. La mención de estas opciones es descriptiva: no implica certificación, afiliación ni respaldo oficial de Oracle.

| Opción | Qué es y dónde encaja | Compatibilidad y consideraciones |
|---|---|---|
| **Spring Boot** | Framework de aplicación para iniciar servicios, aplicaciones web y sistemas empresariales con convenciones, starters, autoconfiguración y un ecosistema de proyectos Spring. Es común usarlo para APIs HTTP, integración, persistencia, seguridad y procesamiento en segundo plano. | La documentación oficial consultada lista Spring Boot 4.1.2 estable y requiere Java 17 como mínimo, con compatibilidad hasta Java 27; también fija rangos de Maven/Gradle y requiere una versión correspondiente de Spring Framework. Esa tabla describe esa release, no todas las ramas. Spring Boot 4.2 aparecía como RC, no estable. Comprueba la página de requisitos y la política de soporte de la rama que elijas [212]. |
| **Jakarta EE** | Familia de especificaciones empresariales (por ejemplo, Servlet, REST, CDI, Persistence, Validation, JSON Processing/Binding). Define contratos para aplicaciones y productos compatibles; por sí sola no es un framework único ni un servidor. Se usa cuando importan APIs normalizadas, despliegue en un runtime compatible o portabilidad entre implementaciones certificadas. | Jakarta EE 11 es una especificación publicada; el sitio oficial mostraba Jakarta EE 12 como trabajo en progreso. Verifica versión de especificación, perfil, servidor compatible y versión Java que soporta ese servidor. No des por hecho que todo servidor implementa todos los perfiles ni que usar APIs Jakarta garantiza portabilidad a extensiones específicas del proveedor [213]. |
| **Quarkus** | Framework orientado a servicios cloud-native, contenedores y Kubernetes, con modos de desarrollo, extensiones y opciones de empaquetado para JVM o imagen nativa. Puede combinar APIs Jakarta con extensiones propias y bibliotecas externas. | Quarkus 3.40 fue anunciado como versión LTS el 30 de septiembre de 2026 y su anuncio establece doce meses de soporte para versiones LTS. La guía de inicio requiere JDK 17+ y una versión concreta de Maven. Las extensiones y la compilación nativa dependen de versión, JDK, toolchain nativa, sistema operativo y arquitectura; una imagen nativa no equivale a un JAR portable [214]. |
| **Micronaut** | Framework para microservicios y aplicaciones cloud-native. Su inyección de dependencias y parte del análisis se realizan durante la compilación, reduciendo trabajo de reflexión en ejecución en ciertos casos. Ofrece módulos HTTP, configuración, datos, seguridad y soporte para servidores/entornos cloud. | Micronaut Framework 5.2.6 fue publicado el 11 de noviembre de 2026 como actualización de seguridad; Micronaut 5 requiere JDK 25 como baseline según su anuncio de la versión mayor [215]. Las ramas 4 y 5 tienen matrices y releases propias; no deduzcas que un módulo Micronaut tiene la misma versión que el framework. Sigue el BOM, notas de versión y avisos de seguridad oficiales [216]. |

Los requisitos del framework no determinan por sí solos el runtime final: pueden imponer condiciones más estrictas las extensiones, el servidor, el driver JDBC, el sistema de construcción o el proveedor JVM. Antes de elegir, prueba el conjunto completo sobre las versiones de Java que de verdad se desplegarán; comprueba migraciones, librerías transitivas, perfiles, imágenes y soporte del proveedor.

#### Categorías de bibliotecas y herramientas frecuentes

El ecosistema cubre más que frameworks web. A continuación, las menciones son ejemplos de productos independientes, no funcionalidades del JDK ni avales oficiales:

| Necesidad | APIs estándar / ejemplos de terceros | Qué comprobar |
|---|---|---|
| HTTP y servicios | `java.net.http`; Spring MVC/WebFlux, RESTEasy/Quarkus REST, clientes y servidores Netty | API bloqueante o reactiva, TLS, límites de conexión y políticas de soporte. |
| Persistencia y acceso a datos | JDBC (`java.sql`); Hibernate ORM, EclipseLink, jOOQ, MyBatis, drivers de base de datos | Compatibilidad del driver con JDK y motor; límites transaccionales, licencias y versión del protocolo. |
| JSON y serialización | Java SE no trae un parser JSON general; Jackson, Gson, JSON-B, JSON-P son opciones de terceros o especificaciones que requieren implementación según el caso | Versionado, comportamiento ante entrada hostil, reflexión/generación y formatos admitidos. |
| Pruebas | `java` no trae una suite de testing unitaria de uso general; JUnit, TestNG, Mockito, AssertJ, REST Assured son herramientas externas | Compatibilidad con runner/plugin, soporte de Java y pruebas aisladas vs. integración. |
| Logging | `java.util.logging`; SLF4J es una fachada externa y Logback/Log4j2, backends externos | Evitar varios bindings/backends simultáneos y controlar datos sensibles en registros. |
| Observabilidad | APIs de gestión/JMX y JFR en JDK; Micrometer, OpenTelemetry y Prometheus en integraciones externas | Formato, coste, protección de endpoints de diagnóstico y compatibilidad entre versiones. |
| GUI | AWT/Swing en `java.desktop`; JavaFX es un proyecto separado que requiere distribución y configuración propias | Sistema operativo, empaquetado, bibliotecas nativas, accesibilidad y proveedor/distribución. |
| Procesamiento de datos | Streams, colecciones y concurrencia estándar; bibliotecas como Apache Commons, Guava o soluciones numéricas especializadas | Coste de memoria, rendimiento medido, API de módulos y licencias. |

Que un artefacto utilice nombres como `javax.*` o `jakarta.*` no dice por sí solo que venga en la instalación del JDK. Paquetes como Java Persistence API y Servlet no forman hoy parte de la biblioteca Java SE del JDK moderno; se obtienen del framework, servidor, especificación y dependencias aplicables. En Jakarta EE 9 se realizó el cambio de namespaces de muchas APIs de `javax.*` a `jakarta.*`, lo que puede ser un cambio de código incompatible. No sustituyas nombres de paquete automáticamente: verifica la versión de la especificación y el framework objetivo.

### Versiones, compatibilidad y soporte

**Versión GA** (*General Availability*) significa que la versión está publicada para uso general; no describe por sí sola duración de mantenimiento. **LTS** es una designación de soporte del proveedor o proyecto, no una propiedad técnica que haga las APIs diferentes. Java 27 es la GA de plataforma más reciente al 18-11-2026; Java 25 es la LTS más reciente. Java 27 no LTS no debe presentarse como “la versión de soporte largo más nueva” [132] [3].

Los ciclos no son uniformes. Oracle declara su roadmap de producto comercial, licencias y soporte para Oracle JDK; OpenJDK define releases de referencia y el desarrollo abierto; Eclipse Adoptium publica Temurin con soporte comunitario y su propio roadmap, que promete al menos cuatro años para sus versiones LTS. Distribuciones de otros proveedores pueden añadir soporte contratado, plazos diferentes, certificaciones, arquitecturas o políticas de actualización. Comprueba siempre proveedor, licencia aplicable, arquitectura, plataforma, frecuencia de parches, fin de disponibilidad y elegibilidad de uso en producción. “Java gratis”, “open source” o “LTS” no resuelven esas diferencias por sí solos [3] [217].

La compatibilidad tiene varias dimensiones:

1. **Fuente y lenguaje:** el compilador debe admitir la sintaxis usada. Las funciones del lenguaje se incorporan por release; el código puede requerir `--enable-preview` si depende de una función preview.
2. **Bytecode:** una JVM debe entender la versión de class file generada. Ejecutar bytecode nuevo en runtime más viejo suele fallar, aunque a veces una compilación con target menor genere clases antiguas.
3. **APIs:** especificar solo un nivel de bytecode antiguo no basta si se compila accidentalmente contra APIs nuevas. `javac --release N` selecciona tanto reglas/API de plataforma de ese release como nivel de bytecode, dentro de las restricciones disponibles del JDK instalado.
4. **Dependencias y framework:** cada biblioteca puede elevar el JDK mínimo o excluir releases recientes. Un framework con compatibilidad anunciada para Java 17–27 no garantiza que todos sus plugins, extensiones o drivers funcionen en los extremos del rango.
5. **Proveedor y sistema:** las implementaciones Java certificadas pueden ofrecer el mismo estándar, pero archivos nativos, certificados, zona horaria, fuentes, GUI, DNS, criptografía, monitorización y builds para CPU/OS pueden variar.

El marcado de versión y soporte debe reproducirse en el proyecto (por ejemplo, versión Java objetivo, wrapper, versiones de plugins, BOM y archivos de bloqueo cuando correspondan). Documenta también la versión mínima de runtime y prueba en el proveedor/plataforma prevista. Una aplicación puede compilar con JDK 27 y tener como objetivo Java 17; no significa que incorpore automáticamente soporte o rendimiento de cada feature de Java 27.

#### Funciones estables, preview, incubator y terceros

No todo lo que aparece en una release de JDK tiene el mismo contrato. Una API o característica final de Java SE se rige por la especificación de esa versión. Las **preview features** están especificadas e implementadas, pero son temporales y requieren activación; pueden cambiar o desaparecer y no hay garantía de compatibilidad desde una versión a la siguiente. Las **incubator APIs** son APIs no finalizadas dentro de módulos `jdk.incubator.*`; pueden evolucionar o retirarse. OpenJDK explica explícitamente ambas categorías y su distinta madurez [144] [74].

JDK 27 incluye, entre otros, preview de patrones con tipos primitivos, concurrencia estructurada y constantes lazy; la Vector API permanece incubator (`jdk.incubator.vector`) en esta release. No son una base estable para una guía de producción portable solo por estar presentes en un JDK GA. En código de prueba, revisa el estado de cada JEP y las opciones de compilación/ejecución específicas. Para producción, prefiere APIs finales salvo que exista una decisión consciente de asumir los cambios, limitar proveedor/JDK y mantener pruebas de migración [94] [144] [74].

Las bibliotecas/frameworks de terceros tampoco se vuelven estables por residir en Maven Central. Busca señales verificables: releases regulares, política de versiones y soporte, avisos de seguridad, compatibilidad de JDK, documentación mantenida, licencia clara, comunidad y capacidad de migración. Una dependencia `SNAPSHOT`, `alpha`, `beta`, `milestone`, `RC` o `-SNAPSHOT` es preliminar respecto a la GA de esa línea; confirma las convenciones particulares del proyecto antes de incluirla en una aplicación productiva.

### Documentación oficial, aprendizaje y comunidad

Utiliza fuentes acordes con la pregunta. La especificación del lenguaje y la JVM define reglas normativas; el JavaDoc explica contratos de APIs; JEP y notas de versión documentan propuestas, estado y cambios; guías de framework resuelven sus convenciones y requisitos. En todos los casos abre la documentación de la versión que usa el proyecto.

- **Java SE/JDK:** documentación versionada de Oracle para API, lenguaje, herramientas, migración, seguridad y notas de versión; `dev.java` para tutoriales y guías de aprendizaje; JLS y JVM Specification para reglas formales [94] [207] [218].
- **OpenJDK:** JEPs, proyectos, calendarios de release, código fuente y listas de correo. Un JEP puede ser propuesta o feature aceptada, preview o incubator; consulta su estado, no solo su título [132] [144] [74].
- **Proveedores JDK:** Oracle Java Downloads y roadmap; Eclipse Adoptium/Temurin para descargas, compatibilidad por plataforma y soporte comunitario. Son distribuciones distintas: comprueba licencia y política del binario que eliges [3] [217].
- **Construcción y dependencias:** manual oficial Apache Maven, historial de releases; manual/matriz oficial de Gradle; documentación Central de Sonatype y portal Central para encontrar coordenadas [208] [209] [210] [211].
- **Frameworks:** documentación y notas de versión de Spring, Eclipse Jakarta EE, Quarkus y Micronaut, incluidas matrices de requisitos, migraciones, soporte y avisos. No extrapoles soporte de una versión mayor a otra [212] [213] [214] [216].
- **Comunidad y formación:** OpenJDK, comunidades de proyecto y foros oficiales, grupos de usuarios Java (JUG), conferencias y espacios de discusión del framework. Stack Overflow y blogs pueden ayudar a encontrar problemas similares, pero contrasta respuestas antiguas con la documentación oficial vigente.

### Flujo profesional para añadir una biblioteca o framework

1. Identifica el requisito: capacidad, protocolo, restricciones de despliegue y datos que se van a manejar. Comprueba primero si una API Java SE cubre el caso.
2. Busca candidatos en la documentación del ecosistema y repositorio apropiado. Confirma que el artefacto y dominio de publicación corresponden al proyecto esperado; los nombres similares no garantizan identidad.
3. Evalúa mantenimiento, release estable, Java mínimo, versiones de framework/build compatibles, licencia, changelog, política de soporte y avisos de seguridad. No selecciones por número de estrellas o porque aparezca en una búsqueda.
4. Añade la dependencia directamente con versión controlada. Si una plataforma ofrece BOM, usa el BOM recomendado en vez de inventar una matriz de versiones; evita importar plataformas incompatibles en paralelo.
5. Inspecciona el grafo (`mvn dependency:tree` o `./gradlew dependencies`), ejecuta pruebas y análisis de dependencias adoptados por el proyecto. Revisa transitive dependencies y exclusiones; no excluyas una dependencia de seguridad o funcionamiento sin comprender su propósito.
6. Registra el cambio, actualiza documentación del proyecto y verifica desde una instalación limpia/CI con el wrapper y JDK objetivo. Prepara actualizaciones periódicas y una ruta de retirada o reemplazo para bibliotecas críticas.

**Cuándo se utiliza:** usa biblioteca estándar para capacidades generales y portables; biblioteca externa cuando aporta una función que el proyecto realmente necesita y su coste de mantenimiento es aceptable; framework cuando sus convenciones, modelo de ejecución e integración reducen trabajo en una aplicación de esa categoría. Si un sistema debe ejecutarse en un servidor Jakarta EE certificado, por ejemplo, el contrato de la especificación y el producto compatible importan más que adoptar un framework solo por popularidad.

### Errores frecuentes y recomendaciones finales

| Error | Por qué causa problemas | Recomendación |
|---|---|---|
| Confundir Java SE, JDK, JVM, Maven Central y framework | Son componentes y responsabilidades diferentes; se aplican distintos ciclos y licencias. | Especifica qué capa y producto describes antes de afirmar soporte o compatibilidad. |
| Llamar “oficial” a una biblioteca de terceros porque es popular o está en Central | La publicación no implica respaldo, certificación ni auditoría de Oracle. | Nombra el proyecto/proveedor y comprueba su fuente y licencia. |
| Equiparar GA y LTS | GA indica disponibilidad; LTS describe un compromiso de soporte con alcance definido por proveedor. | Indica versión, proveedor, estado y fecha de corte. |
| Adoptar preview/incubator como API estable | Puede cambiar o eliminarse, y exigir flags especiales. | Verifica el JEP y elimina estas dependencias en código portable de producción salvo decisión documentada. |
| Fijar solo la versión del JDK local | IDE, CI, Maven/Gradle y producción pueden usar JVM distintas. | Versiona wrappers/toolchains y prueba en runtime de destino. |
| Declarar dependencias sin controlar transitivas | Puede incorporar versiones antiguas, conflictos o componentes con vulnerabilidades. | Audita grafo, actualiza y prueba; no confíes en resolución “latest” implícita. |
| Elegir versión de Spring/Quarkus/Micronaut sin revisar su BOM | Mezclar generaciones o plugins incompatibles puede romper compilación o ejecución. | Sigue la matriz y BOM de la versión exacta y lee la guía de migración. |
| Suponer que `--release` resuelve todos los requisitos | No cambia los requisitos mínimos de dependencias, framework o runtime, ni convierte APIs nuevas en disponibles en runtime viejo. | Comprueba bytecode, API, dependencias y JVM efectiva por separado. |
| Asumir que JDK 27 ofrece binarios idénticos para todos los OS/CPU | Cada proveedor publica artefactos por sistema y arquitectura; puede haber plataformas que no se soporten. | Verifica el binario de proveedor concreto. En Temurin 27, por ejemplo, no hay build para macOS x64/Intel según su anuncio [217]. |

Para un proyecto nuevo con requisitos empresariales, elige primero el runtime y ciclo de soporte acordes con el producto; después confirma que compilador, wrapper, framework, plugins y dependencias soportan esa combinación. Para aprendizaje, trabaja con una LTS vigente salvo que el objetivo sea estudiar una feature del release más reciente. La decisión es de arquitectura y mantenimiento, no una declaración de que un framework o proveedor sea universalmente “el mejor”.

## 16. Buenas prácticas y calidad del código

### 16.1 Qué significa calidad del código

La **calidad del código** es la facilidad con la que un equipo puede entender, probar, cambiar y operar un programa sin introducir defectos evitables. No es una puntuación única ni equivale a seguir un estilo visual. Incluye decisiones de diseño, nombres, contratos explícitos, control de estado, pruebas, documentación útil, análisis automático y revisión humana.

Las prácticas de este capítulo son reglas de equipo, no leyes universales. Para el estilo sintáctico, conviene adoptar una guía conocida —por ejemplo, la de Google o el estilo de OpenJDK— y aplicarla consistentemente. La guía Java de Oracle sobre convenciones es útil para rastrear convenciones históricas, pero la propia página de nombres avisa que es material archivado, revisado por última vez en 1999; no debe presentarse como normativa vigente [219] [45].

Una política razonable tiene reglas explícitas, herramientas ejecutables de forma repetible y excepciones justificadas. Conviene automatizar lo mecánico (formato, nombres y patrones comunes) y reservar la revisión humana para contratos, diseño, legibilidad y adecuación al problema. Ninguna herramienta demuestra que el programa cumple el requisito.

### 16.2 Convenciones de nombres

Los identificadores deben explicar su propósito y distinguir conceptos del dominio. Java diferencia mayúsculas y minúsculas: `totalPedido` y `TotalPedido` son identificadores diferentes. Usa nombres descriptivos en español o en inglés según la convención acordada por el equipo; lo importante es no mezclar idiomas sin motivo y mantener términos del dominio consistentes.

| Elemento | Convención habitual | Ejemplos |
|---|---|---|
| Paquete | Minúsculas, sin guiones; normalmente dominio invertido y nombre del producto | `com.ejemplo.pedidos` |
| Clase, interfaz, enum, record | `UpperCamelCase`; sustantivo o frase nominal | `Pedido`, `RepositorioPedidos`, `EstadoPedido`, `Direccion` |
| Método | `lowerCamelCase`; verbo o acción | `calcularTotal()`, `buscarPorId()` |
| Variable, parámetro y componente de record | `lowerCamelCase`; nombre concreto | `precioUnitario`, `fechaCreacion` |
| Constante realmente constante (`static final`) | Mayúsculas con guion bajo | `MAX_INTENTOS`, `TASA_IMPUESTO` |
| Tipo genérico | Letras breves solo cuando la convención es clara; nombres descriptivos si mejora la lectura | `<T>`, `<K, V>`, `<Respuesta>` |

Un valor `static final` solo merece nombre en mayúsculas si representa una constante semántica y estable; no conviertas automáticamente cada campo final en `MAX_...`. Los nombres de interfaz suelen expresar una capacidad o rol (`Comparable`, `Cerrable`), pero no es necesario añadir `I` como prefijo. Evita abreviaturas inventadas (`calcTotPed`) y nombres vacíos (`data`, `manager`, `object`) si no describen el significado real. `i` puede ser apropiado como índice local en un bucle pequeño; no como nombre de un concepto de negocio.

```java
// Difícil de entender: las abreviaturas y el booleano no revelan el criterio.
boolean ok(P p) {
    return p.t() > 0;
}

// Mejor: la operación y su condición quedan expresadas.
boolean tieneSaldoDisponible(Pedido pedido) {
    return pedido.total().signum() > 0;
}
```

En APIs públicas, cambiar un nombre puede romper código cliente. Antes de renombrar, considera compatibilidad binaria y de fuente, deprecación y migración. En código privado, renombrar para ganar claridad suele ser una refactorización de bajo riesgo si las pruebas cubren el comportamiento.

### 16.3 Encapsulación: proteger invariantes y reducir acoplamiento

**Encapsular** significa ocultar decisiones internas y exponer operaciones que preservan las reglas del objeto. No es solamente poner los campos como `private`: una clase bien encapsulada limita qué estado se puede observar o cambiar y valida las transiciones en un lugar controlado.

Java ofrece accesos `private`, de paquete (sin modificador), `protected` y `public`; los módulos también delimitan qué paquetes exportan. La JLS distingue control de acceso de alcance y define las reglas de visibilidad de declaraciones [220]. Empieza con la visibilidad más estrecha que satisfaga el diseño. Expón una interfaz o método de negocio en vez de permitir que cualquier llamador escriba directamente en los campos. `protected` no equivale a “privado para subclases” en todos los escenarios de paquetes: úsalo con intención y documenta los puntos de extensión.

```java
import java.math.BigDecimal;
import java.util.Objects;

public final class Monedero {
    private BigDecimal saldo;

    public Monedero(BigDecimal saldoInicial) {
        this.saldo = Objects.requireNonNull(saldoInicial, "saldoInicial");
        if (saldoInicial.signum() < 0) {
            throw new IllegalArgumentException("El saldo no puede ser negativo");
        }
    }

    public BigDecimal saldo() {
        return saldo;
    }

    public void ingresar(BigDecimal importe) {
        Objects.requireNonNull(importe, "importe");
        if (importe.signum() <= 0) {
            throw new IllegalArgumentException("El importe debe ser positivo");
        }
        saldo = saldo.add(importe);
    }
}
```

La clase no permite asignar saldo negativo directamente y concentra la validación en su frontera. `BigDecimal` es inmutable, por lo que devolver `saldo` no filtra una referencia a estado mutable. Para colecciones mutables, no devuelvas directamente el campo: devuelve una copia o una vista no modificable, según el contrato requerido. Un *getter* y *setter* indiscriminados no añaden encapsulación útil si permiten romper las invariantes.

**Errores frecuentes:** campos públicos mutables; setters que aceptan cualquier estado; una clase con muchos getters/setters que convierte su modelo en una estructura pasiva; una excepción de encapsulación justificada solo por facilitar pruebas. Haz verificable el comportamiento mediante métodos públicos significativos, constructores apropiados y pruebas.

### 16.4 Inmutabilidad y estado controlado

Un objeto **inmutable** no cambia de estado observable después de construirse. La inmutabilidad facilita razonar sobre invariantes, compartir valores y evitar interferencias accidentales. En Java, `final` impide reasignar una referencia, pero no vuelve inmutable al objeto referenciado. Tampoco basta con campos finales si una colección mutable se conserva o se expone: la inmutabilidad debe ser profunda o estar protegida mediante copias defensivas.

Para datos simples, prefiere campos `private final`, validación al construir y ausencia de mutadores. `List.copyOf` crea una lista no modificable con los elementos de la colección; no hace inmutables los objetos que contiene. Rechaza valores `null`, diferencia que debe estar de acuerdo con el contrato [221].

```java
import java.util.List;
import java.util.Objects;

public final class Etiquetas {
    private final List<String> valores;

    public Etiquetas(List<String> valores) {
        this.valores = List.copyOf(Objects.requireNonNull(valores, "valores"));
    }

    public List<String> valores() {
        return valores;
    }
}
```

La copia evita que el llamador modifique `Etiquetas` al cambiar la lista original, y la lista devuelta rechaza modificaciones. Si los elementos son mutables, todavía podrían cambiar desde otra referencia: considera elementos inmutables, copias de esos elementos o un contrato explícito. No confundas `Collections.unmodifiableList(lista)` —vista no modificable respaldada por la lista original— con una copia aislada.

En código mutable que lo necesita, mantén el estado privado, define quién puede cambiarlo y valida cada transición. `volatile` y `final` tienen semántica de memoria concreta; no son remedios generales para carreras ni sustituyen sincronización o diseño seguro para concurrencia.

### 16.5 Composición antes que herencia por conveniencia

La **composición** construye una funcionalidad combinando objetos que colaboran; la **herencia** define un subtipo que adquiere contrato y comportamiento de su supertipo. Favorece composición cuando el objeto “usa” un servicio y reserva herencia para una relación genuina “es-un”, sustituible según el contrato del supertipo. Las clases concretas abiertas a herencia crean compromisos sobre métodos sobrescribibles y el orden de llamadas; si no se diseñan y documentan para extensión, `final` puede comunicar que no son extensibles.

```java
import java.math.BigDecimal;
import java.util.Objects;

interface PoliticaDescuento {
    BigDecimal aplicar(BigDecimal subtotal);
}

final class ServicioPedidos {
    private final PoliticaDescuento politica;

    ServicioPedidos(PoliticaDescuento politica) {
        this.politica = Objects.requireNonNull(politica, "politica");
    }

    BigDecimal total(BigDecimal subtotal) {
        return politica.aplicar(subtotal);
    }
}
```

`ServicioPedidos` delega el cálculo a una estrategia; se puede reemplazar la política sin crear una jerarquía de subclases. En producción, se puede exponer un constructor público o usar inyección mediante un contenedor si el proyecto realmente lo necesita. Evita interfaces creadas únicamente para cada clase sin que haya variación, sustitución o un límite de arquitectura que las justifique.

### 16.6 SOLID, DRY y KISS en contexto

Estos principios son heurísticas para detectar costes de cambio, no pruebas de corrección ni mandatos para generar capas en todo proyecto. Aplícalos cuando resuelvan un problema observable y comprueba que el diseño no termina siendo más difícil de entender que el problema original.

- **S — Responsabilidad única:** reúne en una clase las decisiones que cambian por el mismo motivo; evita mezclar, por ejemplo, cálculo de negocio, persistencia y presentación si esas responsabilidades evolucionan por separado. No significa “una clase por método”.
- **O — Abierto/cerrado:** permite añadir variantes sin modificar repetidamente un núcleo estable, a menudo mediante una interfaz o estrategia. No anticipes toda variación hipotética con una jerarquía especulativa.
- **L — Sustitución de Liskov:** una implementación debe respetar los contratos esperados del supertipo. No sobrescribas un método de forma que invalide sus precondiciones, postcondiciones o invariantes.
- **I — Segregación de interfaces:** prefiere interfaces enfocadas a una interfaz grande que obliga a clientes a implementar métodos que no usan. El tamaño depende del propósito real de los clientes.
- **D — Inversión de dependencias:** la lógica de alto nivel debe depender de contratos estables, no quedar acoplada directamente a detalles reemplazables. En Java puede lograrse con interfaces y constructores; no exige un framework de inyección.
- **DRY (Don't Repeat Yourself):** evita duplicar conocimiento que debe mantenerse coherente. Dos líneas parecidas no siempre representan el mismo concepto; abstraer prematuramente puede acoplar requisitos que deberían evolucionar por separado.
- **KISS (Keep It Simple, Stupid):** elige la solución más sencilla que cubre los requisitos presentes, con nombres, contratos y límites claros. “Simple” no significa omitir validación, pruebas o tratamiento de errores.

Una abstracción es valiosa cuando reduce duplicación conceptual y facilita un cambio probable. Si oculta el flujo real, multiplica indirectamente llamadas o obliga a entender una jerarquía extensa para modificar una regla, simplifícala. No optimices por reducir líneas de código.

### 16.7 Javadoc y comentarios útiles

**Javadoc** es la documentación vinculada a declaraciones Java mediante comentarios `/** ... */`; la herramienta `javadoc` genera páginas HTML para API. En JDK 25 el *standard doclet* también reconoce comentarios de documentación Markdown `///`, pero para proyectos con herramientas o versiones objetivo heterogéneas, `/** ... */` suele ser la opción más interoperable [222].

Documenta la API pública y los contratos no evidentes: propósito, unidades y rangos, si un argumento puede ser `null`, valores devueltos, efectos observables, excepciones y condiciones de uso. `@param`, `@return`, `@throws`, `@since`, `@deprecated`, `{@link ...}` y `{@code ...}` expresan información estructurada. Escribe una primera oración breve que describa la declaración. Evita copiar la firma en prosa o explicar cada línea: comentarios obsoletos pueden ser más dañinos que su ausencia.

```java
/**
 * Calcula el precio final de un pedido antes del envío.
 *
 * @param subtotal importe no negativo expresado en la moneda del pedido
 * @return subtotal después de aplicar la política configurada
 * @throws IllegalArgumentException si {@code subtotal} es negativo
 */
BigDecimal calcularSubtotalFinal(BigDecimal subtotal) {
    // Implementación omitida en este ejemplo de contrato.
    return subtotal;
}
```

Ejecuta Javadoc con revisión de errores de documentación. Por ejemplo, para una estructura de fuentes que exporta sus clases en un paquete:

```bash
javadoc -Xdoclint:all -d target/apidocs src/main/java/com/ejemplo/pedidos/*.java
```

Salida esperada en una ejecución correcta: se crea documentación HTML bajo `target/apidocs`; la herramienta puede informar progreso y los detalles dependen del JDK y del paquete. Aquí se proporciona como comando, no como ejecución verificada. `-Xdoclint:all` ayuda a encontrar etiquetas o HTML mal formados, pero no determina si el texto es preciso.

### 16.8 Formato y legibilidad

El formato debe poder mantenerse automáticamente. Acordad uso de llaves, sangría, líneas en blanco, orden de miembros, imports, ancho aproximado de línea y codificación; configurad el mismo formato en el IDE y en integración continua. Google Java Style, por ejemplo, define dos espacios de sangría y un límite de cien caracteres; es una opción concreta, no una convención universal [219]. El estilo de OpenJDK y otras guías pueden diferir. Evita mezclar reglas en un mismo repositorio.

```java
// Más difícil de revisar: flujo comprimido y omisión de llaves.
if (pedido != null) total=pedido.total(); else total=BigDecimal.ZERO;

// Más legible: nombres y ramas visibles.
if (pedido != null) {
    total = pedido.total();
} else {
    total = BigDecimal.ZERO;
}
```

Usa una sentencia por línea, llaves incluso cuando el bloque tenga una sola sentencia, espacios consistentes y líneas en blanco para separar etapas lógicas. Envuelve expresiones largas alrededor de operadores de manera que las dependencias queden claras. No alinees columnas con espacios manuales ni uses formato como sustituto de descomponer un método demasiado complejo. Los formateadores como `google-java-format` son herramientas externas: fijad su versión y aceptad la salida automática como estándar del repositorio.

### 16.9 Análisis estático y herramientas de calidad

El **análisis estático** inspecciona el fuente o bytecode sin ejecutar los casos de uso normales. Cada herramienta cubre defectos distintos; su valor depende de las reglas, versión, configuración y falsos positivos aceptados. Automatiza gradualmente y exige revisión a las supresiones con una razón específica.

| Herramienta | Dónde ayuda | Límites y dependencias |
|---|---|---|
| Checkstyle | Convenciones de nombres, imports, Javadoc, llaves y espacios; reglas configurables de fuente | No es un comprobador semántico completo; una regla excesiva puede generar ruido. Es tercero y su integración Maven tiene versión propia. |
| SpotBugs | Patrones de errores probables a partir de bytecode compilado | No detecta todos los defectos ni entiende por completo la intención; resultados son hallazgos que hay que revisar. Es tercero. |
| Error Prone | Errores de programación detectables durante la compilación con `javac` y comprobaciones configurables | Es un complemento del compilador, no una garantía; configuración, compatibilidad con JDK/compilador y opciones de acceso a internals importan. La documentación actual requiere JDK 21 o superior para ejecutarlo [223] [224]. |
| `javac -Xlint` | Advertencias del compilador sobre categorías habilitadas | Complementa, no reemplaza, las herramientas anteriores. Disponible con el JDK. |

Checkstyle publica conjuntos como Google, OpenJDK y Sun. En el corte consultado su sitio anunciaba Checkstyle 14.4.0, y el Maven Checkstyle Plugin documentaba la versión 3.6.0; el plugin puede usar otra versión de Checkstyle si no se configura expresamente [225] [226]. SpotBugs documentaba la integración Maven `spotbugs-maven-plugin` 4.10.5.0 en la página consultada [227]. Son versiones de herramientas, no versiones de Java; verifica compatibilidad con tu JDK, Maven y complemento antes de fijarlas.

En un proyecto Maven que ya tenga la configuración pertinente, estos comandos ilustran el ciclo:

```bash
mvn test
mvn checkstyle:check
mvn spotbugs:check
mvn verify
```

`mvn test` ejecuta las fases previas y pruebas según el ciclo de vida configurado. `checkstyle:check` falla por violaciones solo si el plugin/configuración así lo define. `spotbugs:check` requiere plugin declarado y usa bytecode de compilación. `verify` ejecuta las verificaciones enlazadas a esa fase; no activa automáticamente todos los análisis si no están configurados. En un proyecto real, declara las versiones de plugins en el `pom.xml` y liga las verificaciones a fases de ciclo de vida para que CI y el equipo ejecuten las mismas reglas. Apache distingue el objetivo de informe `checkstyle:checkstyle` de `checkstyle:check`, que puede hacer fallar el build [226].

**Salida representativa, no transcripción verificada:** si las comprobaciones pasan, Maven termina con `BUILD SUCCESS`; si fallan, puede terminar con `BUILD FAILURE` seguido de ubicaciones de fuente, reglas o patrones detectados. El texto concreto cambia por versiones, configuración, sistema operativo y locale. No ignores una advertencia de forma masiva; desactiva solo reglas justificadas y deja registrada la decisión.

#### Usar Error Prone

Error Prone integra comprobaciones con la compilación `javac`; la instalación oficial documenta configuración para Maven y exige JDK 21+ para ejecutar las versiones actuales indicadas allí. Algunas integraciones necesitan argumentos `--add-exports`/`--add-opens` sobre internals del compilador, de modo que su configuración y compatibilidad son más sensibles que una herramienta de formato [224]. Para activar una regla de advertencia o error, la forma de bandera documentada es `-Xep:NombreDeRegla:WARN` o `-Xep:NombreDeRegla:ERROR`; Error Prone pasa parámetros desde `compilerArgs` del `maven-compiler-plugin` [228].

```xml
<compilerArgs>
  <arg>-XDcompilePolicy=simple</arg>
  <arg>--should-stop=ifError=FLOW</arg>
  <arg>-Xplugin:ErrorProne -Xep:DeadException:WARN</arg>
</compilerArgs>
```

Este extracto no constituye una configuración Maven completa: requiere agregar la dependencia del procesador `error_prone_core` en `annotationProcessorPaths`, usar la integración adecuada al JDK y atender los argumentos adicionales que indique la documentación vigente. No copies `--add-exports` indiscriminadamente ni supongas que el mismo `pom.xml` funciona con cualquier vendor o JDK. Prueba una compilación limpia y fija las versiones. Al subir un hallazgo a error, corrige primero el código o documenta una excepción puntual; no relajes todo el análisis por una sola incompatibilidad.

### 16.10 Refactorización demostrativa: de procedimiento acoplado a tipos con contratos

**Refactorizar** es cambiar la estructura interna del código sin cambiar el comportamiento observable, salvo que se acompañe explícitamente de un cambio funcional. El siguiente “antes” concentra representación, validación y cálculo, expone datos sin tipo y usa números mágicos:

```java
// Antes: ejemplo deliberadamente mejorable.
class PedidoViejo {
    public String cliente;
    public double precio;
    public int cantidad;

    public double total() {
        return precio * cantidad * 0.9;
    }
}
```

Problemas: campos públicos permiten estados inválidos; `double` puede introducir errores de redondeo en importes decimales; `0.9` oculta una regla; no se expresa moneda ni unidad; una clase mutable puede cambiar mientras se usa.

**Después**, si el concepto es una línea de pedido y el descuento es una regla explícita, se puede usar un record de datos y una clase que encapsule el comportamiento. El ejemplo es compatible con Java 17+ y usa APIs estables; el objetivo recomendado de esta guía es Java 25. La lista se copia al construir, y los elementos `LineaPedido` son records con componentes inmutables (`String` y `BigDecimal`):

```java
import java.math.BigDecimal;
import java.util.List;
import java.util.Objects;

record LineaPedido(String descripcion, int cantidad, BigDecimal precioUnitario) {
    LineaPedido {
        Objects.requireNonNull(descripcion, "descripcion");
        Objects.requireNonNull(precioUnitario, "precioUnitario");
        if (cantidad <= 0 || precioUnitario.signum() < 0) {
            throw new IllegalArgumentException("Cantidad o precio no válidos");
        }
    }

    BigDecimal subtotal() {
        return precioUnitario.multiply(BigDecimal.valueOf(cantidad));
    }
}

final class Pedido {
    private final String cliente;
    private final List<LineaPedido> lineas;

    Pedido(String cliente, List<LineaPedido> lineas) {
        this.cliente = Objects.requireNonNull(cliente, "cliente");
        this.lineas = List.copyOf(Objects.requireNonNull(lineas, "lineas"));
    }

    BigDecimal subtotal() {
        return lineas.stream()
                .map(LineaPedido::subtotal)
                .reduce(BigDecimal.ZERO, BigDecimal::add);
    }

    BigDecimal totalConDescuento(BigDecimal descuento) {
        Objects.requireNonNull(descuento, "descuento");
        if (descuento.signum() < 0 || descuento.compareTo(BigDecimal.ONE) > 0) {
            throw new IllegalArgumentException("El descuento debe estar entre 0 y 1");
        }
        return subtotal().multiply(BigDecimal.ONE.subtract(descuento));
    }

    String cliente() {
        return cliente;
    }
}

class EjemploPedido {
    public static void main(String[] args) {
        var linea = new LineaPedido("Libro", 2, new BigDecimal("12.50"));
        var pedido = new Pedido("Ada", List.of(linea));
        System.out.println(pedido.totalConDescuento(new BigDecimal("0.10")));
    }
}
```

Salida esperada:

```text
22.5000
```

**Verificación realizada:** el ejemplo integral se compiló con `javac --release 17` y OpenJDK 21.0.13.1, y se ejecutó con `java`; la salida fue `22.5000`. Esto verifica la compatibilidad del ejemplo con ese JDK y nivel de destino, no con cada proveedor ni con JDK 25.

El resultado de `BigDecimal` conserva la escala resultante de sus operaciones; si la presentación exige dos decimales, define redondeo y moneda en la capa de negocio/presentación de acuerdo con la política contable. `var` se usa únicamente para variables locales cuyo tipo se ve en el inicializador; no reemplaza tipos explícitos en API pública. El record no vuelve automáticamente inmutables los objetos mutables que se usen como componentes: sus valores son superficialmente inmutables. En este ejemplo los componentes elegidos son valores inmutables [41] [221].

Los records modelan agregados de datos transparentes: su estado y API quedan ligados al encabezado; el compilador deriva constructor canónico, accesores, `equals`, `hashCode` y `toString`. No son sustituto universal de clases con identidad, ciclos de vida, mutaciones controladas o representación interna que conviene ocultar [41] [229].

**Secuencia prudente de refactorización:** añade o identifica pruebas que describan el comportamiento existente; aplica un cambio estructural pequeño; ejecuta compilación y pruebas; revisa el diff; luego repite. No combines una gran reorganización con cambios de comportamiento sin separarlos en commits o pasos revisables. Una prueba que solo refleja la implementación puede congelar un diseño malo; cubre contratos y casos límite observables.

### 16.11 Pruebas, revisión de código y calidad continua

Las pruebas hacen verificables los contratos. Para lógica de dominio, una prueba unitaria debe comprobar un resultado o una excepción sin depender innecesariamente de red, reloj o base de datos. Las pruebas de integración verifican que componentes reales colaboren. La cobertura indica qué código se ejecutó, no si las aserciones detectaron errores. Los *mocks* sustituyen colaboradores cuando el aislamiento es útil; no simules cada objeto interno, pues eso vuelve las pruebas frágiles.

Ejemplo con JUnit Jupiter (biblioteca externa; JUnit 6 requiere JDK 17+ para ejecutarse). Las versiones y dependencias deben declararse en Maven o Gradle y alinearse con la herramienta de construcción. JUnit publica sus artefactos Maven, incluida la dependencia agregadora `org.junit.jupiter:junit-jupiter`, en Maven Central [230] [231].

```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import static org.junit.jupiter.api.Assertions.assertThrows;

import java.math.BigDecimal;
import java.util.List;
import org.junit.jupiter.api.Test;

class PedidoTest {
    @Test
    void calculaTotalConDescuento() {
        var pedido = new Pedido(
                "Ada",
                List.of(new LineaPedido("Libro", 2, new BigDecimal("12.50"))));

        assertEquals(
                0,
                new BigDecimal("22.5000")
                        .compareTo(pedido.totalConDescuento(new BigDecimal("0.10"))));
    }

    @Test
    void rechazaDescuentoSuperiorAlCienPorCiento() {
        var pedido = new Pedido(
                "Ada",
                List.of(new LineaPedido("Libro", 1, new BigDecimal("10.00"))));

        assertThrows(
                IllegalArgumentException.class,
                () -> pedido.totalConDescuento(new BigDecimal("1.01")));
    }
}
```

`BigDecimal.equals` también compara escala (`2.0` no es igual a `2.00`), por lo que aquí `compareTo` verifica equivalencia numérica. Salida esperada al ejecutar la suite correctamente: dos pruebas aprobadas; en Maven el resumen depende del proveedor Surefire y de la versión de JUnit. Una ejecución fallida debe orientar hacia el método y la aserción, no ocultarse con pruebas deshabilitadas.

En una **revisión de código** pregunta si los nombres reflejan el dominio; si los objetos preservan invariantes; si existe una alternativa más simple; si las mutaciones y efectos secundarios son visibles; si los límites entre módulos son adecuados; si las pruebas cubren resultado normal, bordes y errores; si la API/documentación promete lo que la implementación cumple; y si se añadieron dependencias, complejidad o datos sensibles sin necesidad. La revisión no es una competencia de estilo: comentarios deben referirse a impacto técnico y ofrecer alternativas concretas.

Adopta una lista corta de controles repetibles, por ejemplo: formato automático; compilación con `--release` explícito; pruebas; Checkstyle; SpotBugs; Error Prone donde su JDK y configuración sean compatibles; revisión humana. Establece umbrales gradualmente y conserva las justificaciones de las supresiones. El tiempo de ejecución, los resultados de análisis, el formateo y las pruebas pueden variar por JDK vendor, sistema operativo, versión de herramientas, locale y opciones del build; registra versiones en el proyecto y usa CI reproducible.

### 16.12 Errores frecuentes y recomendaciones

- **Confundir `final` con inmutabilidad profunda.** `final List<X>` impide reasignar la lista, pero la lista todavía puede mutarse. Copia o expón una colección no modificable, y considera también la mutabilidad de sus elementos.
- **Hacer públicos todos los campos para evitar código repetitivo.** El coste es perder control sobre invariantes y compatibilidad. Expón operaciones con intención de dominio.
- **Aplicar SOLID mecánicamente.** Interfaces, patrones y capas tienen coste. Introduce abstracciones cuando el cambio o la sustitución lo justifican.
- **Abstraer dos líneas parecidas bajo DRY sin comprender su semántica.** Duplicación textual no equivale siempre a duplicación de reglas; compartir una función puede acoplar conceptos que deben divergir.
- **Añadir comentarios que repiten el código.** Documenta contrato, motivo, restricción o decisión no obvia; actualiza/elimina documentación al cambiar comportamiento.
- **Usar análisis automático como aprobación total.** Las herramientas detectan clases limitadas de defectos. Mantén pruebas, revisión, análisis de amenazas y criterio humano según el sistema.
- **Confiar en que `source` y `target` de Maven limitan la API disponible.** Prefiere `--release` o `<maven.compiler.release>`: documenta nivel de lenguaje, bytecode y API de plataforma compatible en conjunto [232].
- **Actualizar JDK o reglas sin fijar versiones ni probar el pipeline.** Fija versión de compilador, plugins y reglas; confirma disponibilidad para el vendor/OS de CI y producción.
- **Tratar LTS como garantía idéntica de todos los proveedores.** Selecciona una distribución con una política de soporte adecuada al producto, revisa sus términos y prueba las mismas opciones de JVM en el sistema operativo de destino.
- **Activar funciones preview por parecer modernas.** Las preview requieren habilitación específica y pueden cambiar o desaparecer; no forman parte de esta sección. Para producción, úsalas solo con evaluación consciente de compatibilidad [144].


## 17. Aplicabilidad entre lenguajes

Los fundamentos —descomponer problemas, elegir algoritmos, modelar datos, probar, depurar y proteger entradas— se transfieren entre lenguajes. Lo que no se transfiere automáticamente son reglas sintácticas, semántica de tipos, gestión de memoria, modelo de concurrencia, empaquetado, APIs y comportamiento de runtime. En Java, reaprende explícitamente tipos estáticos, referencias frente a primitivos, excepciones checked/unchecked, compilación a bytecode, JVM, paquetes/módulos y herramientas Maven/Gradle. Un concepto compartido no implica API idéntica ni igual coste temporal.

| Área | Transferible | Específico que debe reaprenderse en Java |
|---|---|---|
| Algoritmos | Descomposición, invariantes, Big O y casos límite. | Coste concreto de `ArrayList`, `HashMap`, streams y asignaciones en la JVM. |
| Sintaxis | Distinguir expresión, sentencia, bloque y alcance. | Llaves, punto y coma, tipos declarados, modificadores y reglas de compilación. |
| Tipos | Modelar dominios y contratos. | Primitivos/referencias, genéricos, boxing, `null`, conversión numérica y borrado de tipos. |
| Estructuras | Elegir por operaciones requeridas. | Interfaces de `Collection`, contrato `equals`/`hashCode`, orden y complejidad de implementaciones. |
| Modularidad | Cohesión y límites. | Paquetes, classpath, module-path, JAR, Maven/Gradle y JPMS. |
| Memoria | Ciclo de vida de objetos y recursos. | Stack de ejecución, heap administrado por GC, referencias; cerrar recursos explícitamente con `try`-with-resources. |
| Concurrencia | Razones, orden, carreras y comunicación. | Modelo de memoria Java, `Thread`, ejecutores, virtual threads, sincronización y APIs asíncronas. |
| Seguridad | Validación, mínimo privilegio, secretos y actualizaciones. | APIs JCA/JCE, proveedores criptográficos, classloader y cadena de suministro del JDK/dependencias. |
| Pruebas | Aserciones, casos, mocks e integración. | JUnit/Jupiter y herramientas externas; compatibilidad se define en el build. |

No migres mecánicamente patrones de otro lenguaje: primero estudia sus garantías y luego traduce la intención. Referencia normativa: JLS/JVMS; referencia de APIs: Java SE API Specification [6][9][7].

## 18. Ruta pedagógica para estudiar Java

Empieza con Java 25 JDK, terminal y editor. Recorre el primer programa, compilación y ejecución; practica variables, expresiones, condicionales, bucles, métodos, arrays y `String`. Explica en voz alta qué recibe cada fragmento, qué cambia y qué imprime. Usa `jshell` para explorar expresiones pequeñas, sin confundir el REPL con la forma usual de entregar una aplicación.

Después crea tipos propios, clases, interfaces, colecciones y excepciones. Escribe métodos con contratos claros y prueba casos normales, extremos e inválidos. Sigue con archivos, rutas, JSON/CSV con APIs estándar cuando sea posible, módulos y un build Maven o Gradle. Aprende a depurar con breakpoints y stack traces antes de sumar herramientas.

En una tercera etapa, incorpora JUnit, dependencias, logging, análisis estático y control de versiones. Estudia transacciones de recursos, memoria, rendimiento medido, seguridad y concurrencia solo con tareas reales. Finalmente revisa la compatibilidad del target (`--release`/toolchain), despliegue, empaquetado y estrategia de actualización. No es necesario dominar los 16 apartados antes de construir: progresa mediante proyectos pequeños y revisión iterativa.

Para cada concepto: lee la explicación, modifica el ejemplo, predice su resultado, ejecuta en tu propia instalación, escribe pruebas, introduce deliberadamente un error y depúralo. Los ejemplos de este manual no se afirman como ejecutados; los resultados indicados son salidas esperadas a partir del código bajo las condiciones descritas.

## 19. Referencia rápida

| Tarea | Java habitual |
|---|---|
| Compilar fuente | `javac --release 25 Hola.java` |
| Ejecutar clase | `java Hola` |
| Ejecutar fuente simple | `java Hola.java` (modo fuente de un archivo; adecuado para ejemplos, no reemplaza el build de proyecto) |
| Explorar interactivo | `jshell` |
| Entrada de consola | `new Scanner(System.in)`; decidir si se usa `nextLine()` y conversión explícita |
| Declarar variable | `int cuenta = 3;`, `var nombre = "Ada";` (tipo local inferido, no dinámico) |
| Constante | `static final double IVA = 0.21;` |
| Condicional | `if (condicion) { ... } else { ... }` |
| Iterar colección | `for (var elemento : elementos) { ... }` |
| Función/método | `static int doble(int x) { return 2 * x; }` |
| Colección ordenada mutable | `List<String> nombres = new ArrayList<>();` |
| Mapa | `Map<String, Integer> stock = new HashMap<>();` |
| Conjunto | `Set<String> tags = new HashSet<>();` |
| Excepción | `try { ... } catch (IOException e) { ... }` |
| Recurso autocerrable | `try (var reader = Files.newBufferedReader(path)) { ... }` |
| Paquete | `package com.ejemplo;` como primera declaración no comentario |
| Pruebas | JUnit es dependencia de terceros; `javac` no incluye JUnit |

Recuerda: `=` asigna; `==` compara primitivos, pero para igualdad lógica de objetos usa `equals`; `&&` y `||` cortocircuitan, `&`/`|` también pueden operar bit a bit. En Java los nombres distinguen mayúsculas y minúsculas (`String` no es `string`).

## 20. Errores frecuentes

1. **Instalar solo un runtime:** para compilar y usar `javac` instala un JDK, no basta con un runtime reducido.
2. **Confundir JDK, Java SE y proveedor:** Java SE es la plataforma especificada; el proveedor distribuye su build y condiciones. Fija proveedor y versión requeridos en entornos repetibles.
3. **Elegir GA más nueva sin comprobar compatibilidad:** prueba dependencias, plugins, arquitectura y despliegue; no LTS no implica mala calidad, pero sí horizonte distinto de soporte.
4. **Olvidar el nombre de archivo de una clase pública:** `public class Hola` va en `Hola.java` en compilación convencional.
5. **Omitir llaves o punto y coma:** el compilador exige bloques y terminadores según gramática; el IDE no reemplaza entenderlos.
6. **Comparar cadenas con `==`:** compara identidad de referencia; para contenido usa `equals`/`equalsIgnoreCase` según el caso.
7. **Esperar tipo dinámico de `var`:** solo infiere el tipo local en compilación; no permite cambiarlo a otro tipo después.
8. **Desbordar enteros o truncar división:** `5 / 2` entre enteros produce `2`; elige un tipo/cálculo decimal adecuado y controla límites.
9. **Desreferenciar `null`:** modela ausencia, valida límites y evita devolver `null` innecesariamente.
10. **Modificar colección durante iteración:** usa iterador, métodos de colección adecuados o construye una nueva colección; respeta contrato de concurrencia.
11. **Capturar `Exception` para silenciar errores:** captura el tipo que puedes manejar, conserva contexto y no ocultes causa.
12. **Dejar abierto un archivo/socket:** usa `try`-with-resources para recursos `AutoCloseable`.
13. **Añadir dependencias sin evaluar:** declara en Maven/Gradle, fija versiones apropiadas, revisa licencia, mantenimiento y vulnerabilidades.
14. **Usar APIs preview sin marcarlo:** exige flags y tiene garantías de compatibilidad diferentes; para ejemplos portables usa APIs finalizadas.
15. **Creer que un `volatile` hace atómico cualquier operación:** protege visibilidad/orden en casos concretos, pero no vuelve compuesta una lectura-modificación-escritura atómica.
16. **Tratar mayor cobertura como mayor calidad:** mide comportamiento y casos; cobertura no prueba corrección.

## 21. Ejercicios progresivos

Resuelve primero sin consultar las respuestas. Usa Java SE salvo donde se especifique una herramienta externa. Para entradas inválidas, define qué comportamiento esperas antes de codificar.

1. **Saludo:** lee un nombre y escribe `Hola, NOMBRE`; trata una línea vacía.
2. **Conversor:** método Celsius a Fahrenheit; verifica 0 °C → 32 °F y -10 °C → 14 °F.
3. **Contador de palabras:** cuenta palabras ignorando espacios repetidos y determina la frecuencia máxima sin distinguir mayúsculas.
4. **Validador:** método que acepta un entero entre 1 y 100; convierte texto y comunica por separado formato inválido y rango inválido.
5. **Inventario:** mapa de artículo a unidades; implementa suma no negativa y consulta de artículo desconocido.
6. **Cola FIFO:** procesa tres tareas en orden de entrada con `ArrayDeque`.
7. **Archivo de datos:** escribe y lee texto UTF-8 con `Files`; maneja `IOException` sin capturar indiscriminadamente.
8. **Pruebas:** agrega dos pruebas JUnit para una función de descuento, un caso válido y uno inválido. JUnit debe configurarse como dependencia externa.
9. **Frecuencias:** cuenta valores de una lista con `HashMap`; explica tiempo promedio O(n) y espacio O(k), sujeto a hashing/implementación.
10. **Concurrencia:** ejecuta dos tareas bloqueantes simuladas secuencialmente y mediante un executor; agrega timeout y explica por qué dos tareas no demuestran que la concurrencia siempre acelere trabajo.

## 22. Soluciones

Soluciones posibles; no son únicas. Fragmentos autónomos salvo indicación. Los resultados son esperados, no certifican ejecución. El ejercicio 8 requiere JUnit Jupiter externo y el 10 requiere completar el `main` con medición en el equipo propio.

### Ejercicio 1: saludo

```java
import java.util.Scanner;

class Saludo {
    public static void main(String[] args) {
        try (Scanner entrada = new Scanner(System.in)) {
            System.out.print("Nombre: ");
            String nombre = entrada.nextLine().trim();
            if (nombre.isEmpty()) nombre = "invitada";
            System.out.println("Hola, " + nombre);
        }
    }
}
```

Con entrada `Ada`, salida esperada: `Hola, Ada`. Al cerrar `Scanner` se cierra también `System.in`; en aplicaciones con varias lecturas, administra la entrada en el nivel superior y no la cierres antes de tiempo.

### Ejercicio 2: conversión

```java
class Temperatura {
    static double celsiusAFahrenheit(double celsius) {
        return celsius * 9.0 / 5.0 + 32.0;
    }
    public static void main(String[] args) {
        System.out.println(celsiusAFahrenheit(0));
        System.out.println(celsiusAFahrenheit(-10));
    }
}
```

Salida esperada: `32.0` y `14.0`. Se usan literales decimales para evitar división entera.

### Ejercicio 3: contar palabras

```java
import java.util.*;

class FrecuenciaPalabras {
    public static void main(String[] args) {
        String frase = "Java es claro y Java es práctico";
        Map<String, Integer> conteo = new HashMap<>();
        for (String palabra : frase.toLowerCase(Locale.ROOT).trim().split("\s+")) {
            conteo.merge(palabra, 1, Integer::sum);
        }
        var max = conteo.entrySet().stream()
            .max(Map.Entry.comparingByValue()).orElseThrow();
        System.out.println("palabras=" + frase.trim().split("\s+").length);
        System.out.println(max.getKey() + "=" + max.getValue());
    }
}
```

Salida esperada: `palabras=7` y `java=2`. Si hay empate, `HashMap` no promete cuál gana; define una regla de desempate si es requisito.

### Ejercicio 4: validar rango

```java
class Rango {
    static int validar(String texto) {
        final int n;
        try {
            n = Integer.parseInt(texto);
        } catch (NumberFormatException e) {
            throw new IllegalArgumentException("escribe un entero", e);
        }
        if (n < 1 || n > 100) {
            throw new IllegalArgumentException("el entero debe estar entre 1 y 100");
        }
        return n;
    }
}
```

La excepción conserva la causa original cuando falla la conversión; se transforma en `IllegalArgumentException` porque este método define el contrato para sus argumentos.

### Ejercicio 5: inventario

```java
import java.util.HashMap;
import java.util.Map;

class Inventario {
    private final Map<String, Integer> unidades = new HashMap<>();
    void sumar(String articulo, int cantidad) {
        if (cantidad < 0) throw new IllegalArgumentException("cantidad negativa");
        unidades.merge(articulo, cantidad, Integer::sum);
    }
    int consultar(String articulo) { return unidades.getOrDefault(articulo, 0); }
    public static void main(String[] args) {
        var inv = new Inventario(); inv.sumar("cuaderno", 4); inv.sumar("cuaderno", 2);
        System.out.println(inv.consultar("cuaderno"));
        System.out.println(inv.consultar("regla"));
    }
}
```

Salida esperada: `6` y `0`. En sistema real decide si un artículo inexistente equivale a cero o a un error de dominio.

### Ejercicio 6: cola FIFO

```java
import java.util.ArrayDeque;
import java.util.Queue;

class Procesador {
    public static void main(String[] args) {
        Queue<String> cola = new ArrayDeque<>(java.util.List.of("tarea-1", "tarea-2", "tarea-3"));
        while (!cola.isEmpty()) System.out.println("Procesando " + cola.remove());
    }
}
```

Salida esperada: tareas 1, 2 y 3 en ese orden. `ArrayDeque` no acepta `null`.

### Ejercicio 7: archivo UTF-8

```java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

class Archivo {
    public static void main(String[] args) throws IOException {
        Path archivo = Path.of("salida.txt");
        Files.writeString(archivo, "Java: café
", StandardCharsets.UTF_8);
        String contenido = Files.readString(archivo, StandardCharsets.UTF_8);
        System.out.print(contenido);
    }
}
```

Salida esperada: `Java: café`. En producción, decide ubicación, límites de tamaño, permisos, manejo del error y ciclo de vida del archivo.

### Ejercicio 8: pruebas con JUnit Jupiter

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class DescuentoTest {
    static int descuento(int centimos, int porcentaje) {
        if (centimos < 0 || porcentaje < 0 || porcentaje > 100)
            throw new IllegalArgumentException("argumentos fuera de rango");
        return centimos * (100 - porcentaje) / 100;
    }
    @Test void aplicaDescuento() { assertEquals(900, descuento(1000, 10)); }
    @Test void rechazaPorcentajeInvalido() {
        assertThrows(IllegalArgumentException.class, () -> descuento(1000, 101));
    }
}
```

Se requiere configurar JUnit en el build; no forma parte del JDK. El uso de `int` puede desbordar con importes grandes; el ejemplo está acotado al caso didáctico.

### Ejercicio 9: complejidad de frecuencias

```java
import java.util.HashMap;
import java.util.List;
import java.util.Map;

class Conteo {
    static Map<String, Integer> contar(List<String> datos) {
        Map<String, Integer> mapa = new HashMap<>();
        for (String dato : datos) mapa.merge(dato, 1, Integer::sum);
        return mapa;
    }
}
```

Con hashing habitual, el tiempo promedio es O(n) y el espacio O(k), donde `n` es el tamaño de la entrada y `k` el número de claves distintas. Colisiones, funciones `hashCode` costosas y detalles de implementación afectan el coste.

### Ejercicio 10: tareas de E/S

```java
import java.util.concurrent.*;

class Tareas {
    static String simular(String nombre) throws InterruptedException {
        Thread.sleep(100); return nombre;
    }
    public static void main(String[] args) throws Exception {
        try (var pool = Executors.newFixedThreadPool(2)) {
            Future<String> a = pool.submit(() -> simular("A"));
            Future<String> b = pool.submit(() -> simular("B"));
            System.out.println(a.get(2, TimeUnit.SECONDS) + b.get(2, TimeUnit.SECONDS));
        }
    }
}
```

Salida esperada: `AB`. El ejemplo ilustra tareas concurrentes con espera bloqueante, no mide rendimiento ni implica que cualquier carga se beneficie. En proyectos fija explícitamente un timeout total y propaga errores/cancelación según el contrato de servicio.

## 23. Mini proyectos

### Gestor de tareas de consola — principiante

Implementa crear, listar, marcar como completada y eliminar una tarea. Separa un modelo `Tarea`, la lógica de una clase de servicio y el bucle de consola. Añade validación, una colección adecuada y pruebas. Extensión: persistir en JSON con una dependencia externa elegida conscientemente o en un formato simple documentado. Criterios: se conserva el estado durante la sesión, entradas inválidas no corrompen datos y cada operación tiene pruebas.

### Analizador de CSV — intermedio

Lee ventas de un CSV en UTF-8, valida encabezados y filas, calcula cantidades e importes y emite resumen. La biblioteca estándar cubre archivos, pero no proporciona un lector CSV completo con tratamiento genérico de dialectos; decide entre implementar el subconjunto documentado o usar una biblioteca CSV externa (declarada y fijada en el build). Usa `BigDecimal` para dinero, pruebas con archivos temporales, reporte de número de fila inválida y estrategia explícita para archivos grandes. Criterios: no confundir coma decimal/separador, no descartar errores silenciosamente y documentar formato.

### API de catálogo o inventario — intermedio/avanzado

Construye un servicio REST con Spring Boot, Quarkus o Micronaut (terceros, no parte de Java SE). Divide dominio, persistencia y capa HTTP; valida solicitudes; emplea consultas parametrizadas y autenticación/autorización adecuadas; registra eventos sin secretos; aporta pruebas unitarias e integración y dependencias auditables. Escoge un framework, no mezcles tres. Criterios: errores HTTP coherentes, migraciones reproducibles, secretos fuera del repositorio, compatibilidad documentada y empaquetado automatizado.

## 24. Glosario

- **API:** contrato accesible para usar tipos y operaciones de una biblioteca.
- **Bytecode:** instrucciones JVM producidas normalmente por el compilador `javac` y almacenadas en clases/JAR.
- **Classpath:** búsqueda de clases y recursos tradicionales; distinta de `module-path`.
- **Colección:** interfaz/estructura de Java para agrupar elementos; `Map` se organiza como mapa de claves/valores, no extiende `Collection`.
- **Dependencia externa:** componente que el proyecto declara y obtiene aparte del JDK, por ejemplo desde Maven Central.
- **Excepción checked:** excepción comprobada por el compilador que debe capturarse o declararse, con excepciones definidas por `RuntimeException` excluidas.
- **GC (garbage collector):** mecanismo de runtime que recupera heap inalcanzable; no reemplaza cierre de recursos externos.
- **Heap:** zona administrada donde normalmente viven objetos; el modelo de memoria abstracto no debe reducirse a una garantía física de implementación.
- **JAR:** archivo de clases/recursos Java con formato ZIP y metadatos opcionales.
- **Java SE:** especificaciones y APIs base de la plataforma Java Standard Edition.
- **JDK:** kit de desarrollo de un proveedor con compilador, herramientas y componentes de runtime.
- **JLS:** Java Language Specification, especificación del lenguaje.
- **JVM:** máquina virtual que ejecuta bytecode e implementa el modelo de ejecución.
- **LTS:** etiqueta/política de soporte ofrecida por determinados proveedores; plazo y condiciones varían.
- **Maven Central:** repositorio central común de artefactos Java; disponibilidad allí no garantiza seguridad ni calidad.
- **Módulo JPMS:** unidad explícita de dependencias y encapsulación introducida con el sistema de módulos de Java.
- **Primitivo:** tipo elemental como `int` o `boolean`; no es objeto aunque exista autoboxing a su wrapper.
- **Preview:** característica temporal habilitada explícitamente que puede cambiar o desaparecer antes de ser definitiva.
- **Proveedor JDK:** organización que construye/distribuye un JDK y define su soporte/licencia.
- **Referencia:** valor que permite acceder a un objeto; puede ser `null`; no es un puntero aritmético manipulable.
- **Runtime:** entorno necesario para ejecutar bytecode; empaquetado/configuración varía entre distribuciones y versiones.
- **Toolchain:** selección de JDK y opciones de compilación/runtime para construir un proyecto de manera reproducible.
- **Virtual thread:** hilo JVM liviano gestionado por el runtime, definitivo desde Java 21; no es una API preview en Java 25.

## 25. Referencias

Fuentes oficiales y primarias para validar detalles de versión, APIs y herramientas. Las especificaciones y la documentación de versión concreta prevalecen sobre tutoriales generales. Los frameworks y herramientas de terceros deben consultarse en su documentación y licencias actuales.

### 25.1. Java: fundamentos, historia y versiones

- [1. Dev.java: Java Affinity Logo y condiciones de uso](https://dev.java/community/affinity/)
- [2. Documentación oficial](https://openjdk.org/projects/jdk/27/)
- [3. Hoja de ruta de soporte Oracle Java SE actualizada en octubre de 2026](https://www.oracle.com/java/technologies/java-se-support-roadmap.html)
- [4. Documentación oficial](https://www.oracle.com/java/technologies/downloads/)
- [5. Documentación oficial](https://openjdk.org/projects/jdk/)
- [8. Dev.java: tutoriales oficiales de Java](https://dev.java/learn/)
- [11. Preguntas frecuentes oficiales sobre licencias de Oracle Java SE](https://www.oracle.com/java/technologies/javase/jdk-faqs.html)
- [12. Preguntas frecuentes de Eclipse Adoptium sobre Temurin y compatibilidad](https://adoptium.net/docs/faq)
- [13. Java Language Specification: prefacio sobre el origen y propósito de Java](https://docs.oracle.com/javase/specs/jls/se6/jls3.pdf)
- [14. Glosario Oracle de Java JDK JRE y JVM](https://www.oracle.com/java/technologies/glossary.html)
- [17. Oracle: una breve historia de Java](https://www.oracle.com/a/ocom/docs/dc/ww-brief-history-java-infographic.pdf)
- [18. Proyecto JDK de OpenJDK y registro de versiones GA](https://openjdk.org/projects/jdk)
- [19. Oracle JDK releases y calendario de lanzamientos](https://www.oracle.com/java/technologies/update-release-numbers-change.html)
- [24. Oracle Java Technical Details y plataformas Java](https://www.oracle.com/java/technologies)
- [57. Notas oficiales de JDK 27.0.1.1](https://www.oracle.com/java/technologies/javase/27-0-1-1-relnotes.html)
- [125. OpenJDK JDK 28: calendario y acceso anticipado](https://openjdk.org/projects/jdk/28)
- [132. OpenJDK JDK 27 Project: General Availability](https://openjdk.org/projects/jdk/27)
- [143. Notas de publicación del JDK 27](https://www.oracle.com/java/technologies/javase/27-relnote-issues.html)
- [183. OpenJDK JDK 25: GA y estado LTS](https://openjdk.org/projects/jdk/25)
- [193. Java Language Specification, edición Java SE 26](https://docs.oracle.com/javase/specs/jls/se26/html/index.html)
- [218. The Java Language Specification Java SE 27 Edition](https://docs.oracle.com/javase/specs/jls/se27/html/index.html)

### 25.2. Especificaciones del lenguaje, JVM y sintaxis

- [6. Java Language Specification, Java SE 25](https://docs.oracle.com/en/java/javase/25/docs/specs/jls/index.html)
- [9. Java Virtual Machine Specification, Java SE 25](https://docs.oracle.com/en/java/javase/25/docs/specs/jvms/index.html)
- [10. Java Language Specification Java SE 27: capítulo de introducción](https://docs.oracle.com/javase/specs/jls/se27/html/jls-1.html)
- [23. Especificaciones oficiales Java Language Specification y Java Virtual Machine Specification](https://docs.oracle.com/javase/specs)
- [25. Java Language Specification, Java SE 25, Chapter 3: Lexical Structure](https://docs.oracle.com/javase/specs/jls/se25/html/jls-3.html)
- [26. Java Language Specification, Java SE 25, Chapter 14: Blocks, Statements, and Patterns](https://docs.oracle.com/javase/specs/jls/se25/html/jls-14.html)
- [27. Java Language Specification, Java SE 25, Chapter 15: Expressions](https://docs.oracle.com/javase/specs/jls/se25/html/jls-15.html)
- [28. Java Language Specification, Java SE 25, Chapter 7: Packages and Modules](https://docs.oracle.com/javase/specs/jls/se25/html/jls-7.html)
- [31. Java Language Specification Java SE 27: Chapter 4: Types, Values, and Variables](https://docs.oracle.com/javase/specs/jls/se27/html/jls-4.html)
- [32. Java Language Specification Java SE 27: Chapter 5: Conversions and Contexts](https://docs.oracle.com/javase/specs/jls/se27/html/jls-5.html)
- [34. Java Language Specification Java SE 27: Chapter 10: Arrays](https://docs.oracle.com/javase/specs/jls/se27/html/jls-10.html)
- [39. Java Language Specification: Parameterized Types, type arguments and wildcards](https://docs.oracle.com/javase/specs/jls/se27/html/jls-4.html#jls-4.5)
- [46. Especificación del lenguaje Java SE 27: expresiones y operadores](https://docs.oracle.com/javase/specs/jls/se27/html/jls-15.html)
- [47. Especificación del lenguaje Java SE 27: sentencias y control de flujo](https://docs.oracle.com/javase/specs/jls/se27/html/jls-14.html)
- [48. Especificación del lenguaje Java SE 27: declaraciones de clase y métodos](https://docs.oracle.com/javase/specs/jls/se27/html/jls-8.html)
- [49. Especificación del lenguaje Java SE 27: nombres, ámbitos y acceso](https://docs.oracle.com/javase/specs/jls/se27/html/jls-6.html)
- [55. Especificación del lenguaje Java SE 27: excepciones](https://docs.oracle.com/javase/specs/jls/se27/html/jls-11.html)
- [75. Especificación del lenguaje Java SE 25: clases](https://docs.oracle.com/javase/specs/jls/se25/html/jls-8.html)
- [76. Especificación del lenguaje Java SE 25: interfaces funcionales](https://docs.oracle.com/javase/specs/jls/se25/html/jls-9.html)
- [88. Java Language Specification 27: paquetes, imports y unidades de compilación](https://docs.oracle.com/javase/specs/jls/se27/html/jls-7.html)
- [106. Especificación de la Máquina Virtual Java SE 27: estructura y áreas de datos](https://docs.oracle.com/en/java/javase/27/docs/specs/jvms/jvms-2.html)
- [118. Java Language Specification: tipos primitivos y char](https://docs.oracle.com/javase/specs/jls/se25/html/jls-4.html)
- [140. Especificación del lenguaje Java, capítulo 17: hilos y modelo de memoria](https://docs.oracle.com/javase/specs/jls/se27/html/jls-17.html)
- [198. Java Language Specification, Java SE 25: sentencia assert](https://docs.oracle.com/javase/specs/jls/se25/html/jls-14.html#jls-14.10)
- [220. Especificación del lenguaje Java SE 25: nombres y control de acceso](https://docs.oracle.com/javase/specs/jls/se25/html/jls-6.html)

### 25.3. Tipos de datos, clases, objetos y características modernas

- [20. JEP 126: expresiones lambda en Java 8](https://openjdk.org/jeps/126)
- [30. JEP 512: Compact Source Files and Instance Main Methods](https://openjdk.org/jeps/512)
- [33. Java SE 27 API: BigDecimal](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/math/BigDecimal.html)
- [35. Java SE 27 API: Optional<T>](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/Optional.html)
- [36. Java SE 27 API: Integer](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/lang/Integer.html)
- [37. JEP 394: Pattern Matching for instanceof](https://openjdk.org/jeps/394)
- [38. JEP 532: Primitive Types in Patterns, instanceof, and switch (Fifth Preview)](https://openjdk.org/jeps/532)
- [40. JEP 286: Local-Variable Type Inference](https://openjdk.org/jeps/286)
- [41. JEP 395: Records](https://openjdk.org/jeps/395)
- [42. JEP 409: Sealed Classes](https://openjdk.org/jeps/409)
- [43. JEP 441: Pattern Matching for switch](https://openjdk.org/jeps/441)
- [44. JEP 440: Record Patterns](https://openjdk.org/jeps/440)
- [45. Convenciones de nombres Java de Oracle, página archivada](https://www.oracle.com/java/technologies/javase/codeconventions-namingconventions.html)
- [229. API Record de Java SE 25](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/lang/Record.html)
- [219. Guía de estilo Java de Google](https://google.github.io/styleguide/javaguide.html)
- [222. Especificación de comentarios Javadoc para JDK 25](https://docs.oracle.com/en/java/javase/25/docs/specs/javadoc/doc-comment-spec.html)

### 25.4. Colecciones y estructuras de datos

- [50. API Java SE 27: paquete java.util y Collections Framework](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/package-summary.html)
- [51. API Java SE 27: clase ArrayDeque](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/ArrayDeque.html)
- [52. API Java SE 27: clase ArrayList](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/ArrayList.html)
- [53. API Java SE 27: clase HashMap](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/HashMap.html)
- [54. API Java SE 27: clase HashSet](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/HashSet.html)
- [58. Introducción al Collections Framework de Java](https://docs.oracle.com/javase/tutorial/collections/intro/index.html)
- [59. API Map de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/Map.html)
- [60. API LinkedList de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/LinkedList.html)
- [61. API Arrays de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/Arrays.html)
- [62. API List de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/List.html)
- [63. API Deque de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/Deque.html)
- [64. API Set de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/Set.html)
- [65. API TreeSet de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/TreeSet.html)
- [66. API SortedMap de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/SortedMap.html)
- [67. API TreeMap de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/TreeMap.html)
- [68. Contrato de equals y hashCode en Object](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/lang/Object.html)
- [69. API Stack de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/Stack.html)
- [70. API PriorityQueue de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/PriorityQueue.html)
- [71. Sitio oficial de JGraphT y coordenadas Maven](https://jgrapht.org/)
- [72. JEP 431: colecciones secuenciadas](https://openjdk.org/jeps/431)
- [73. Módulo incubador Vector de JDK 27](https://docs.oracle.com/en/java/javase/27/docs/api/jdk.incubator.vector/module-summary.html)
- [74. JEP 11: módulos incubadores](https://openjdk.org/jeps/11)

### 25.5. Programación funcional, streams y programación reactiva

- [77. API Java SE 25: paquete java.util.function](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/function/package-summary.html)
- [78. API Java SE 25: paquete java.util.stream](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/stream/package-summary.html)
- [79. Tutorial de Java: paralelismo en streams](https://docs.oracle.com/javase/tutorial/collections/streams/parallelism.html)
- [80. API Java SE 25: Flow](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/concurrent/Flow.html)
- [81. Reactive Streams: especificación JVM](https://www.reactive-streams.org/)
- [82. Project Reactor 3 Reference Guide](https://projectreactor.io/docs/core/release/reference)
- [83. Maven Central: metadatos de reactor-core](https://repo.maven.apache.org/maven2/io/projectreactor/reactor-core/maven-metadata.xml)
- [84. Spring Framework: Spring WebFlux](https://docs.spring.io/spring-framework/reference/web/webflux.html)
- [149. Paquete Stream de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/stream/package-summary.html)

### 25.6. Paquetes, módulos, importaciones y organización de proyectos

- [15. JEP 220: imágenes modulares de ejecución](https://openjdk.org/jeps/220)
- [21. JEP 261: sistema de módulos de Java](https://openjdk.org/jeps/261)
- [89. Dev.java: introducción a módulos, exports, opens y servicios](https://dev.java/learn/organizing/modules/intro)
- [90. Oracle JAR File Specification: JAR modular y manifiesto](https://docs.oracle.com/en/java/javase/25/docs/specs/jar/jar.html)
- [91. Dev.java: paquetes y organización de tipos](https://dev.java/learn/language/oop/packages)
- [92. Dev.java: módulos, acceso reflectivo y encapsulación](https://dev.java/learn/organizing/modules)
- [93. Dev.java: módulo sin nombre y código del classpath](https://dev.java/learn/organizing/modules/unnamed-module)
- [94. Oracle Java SE 27 API Specification](https://docs.oracle.com/en/java/javase/27/docs/api/index.html)
- [95. Dev.java: compilar, empaquetar y lanzar módulos](https://dev.java/learn/organizing/modules/building)
- [96. Oracle javac: classpath, module-path y opciones de compilación](https://docs.oracle.com/en/java/javase/25/docs/specs/man/javac.html)
- [97. Apache Maven: estructura estándar de directorios](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)

### 25.7. Compilación, ejecución y herramientas del JDK

- [16. Documentación de dev.java sobre el lanzador java](https://dev.java/learn/jvm/core-tools/java)
- [29. Java SE 25 Tool Specification: The java Command](https://docs.oracle.com/en/java/javase/25/docs/specs/man/java.html)
- [68. Dev.java: uso del intérprete de Python](https://dev.java/learn/jvm/core-tools)
- [148. Manual oficial del comando jcmd](https://docs.oracle.com/en/java/javase/27/docs/specs/man/jcmd.html)
- [155. Manual oficial del comando jdb de JDK 27](https://docs.oracle.com/en/java/javase/27/docs/specs/man/jdb.html)
- [179. Java SE 26: especificaciones de herramientas del JDK](https://docs.oracle.com/en/java/javase/26/docs/specs/man)
- [181. Java SE 26: comando java](https://docs.oracle.com/en/java/javase/26/docs/specs/man/java.html)
- [182. Java SE 26: comando javac](https://docs.oracle.com/en/java/javase/26/docs/specs/man/javac.html)
- [192. Java SE 26: herramienta JShell](https://docs.oracle.com/en/java/javase/26/docs/specs/man/jshell.html)
- [207. Dev.java: The Core JDK Tools](https://dev.java/learn/jvm/core-tools)

### 25.8. Maven, Gradle y gestión de dependencias

- [98. Gradle 9.9.1: plugin Java, source sets y módulo Java](https://docs.gradle.org/current/userguide/java_plugin.html)
- [99. Apache Maven: fases del ciclo de vida de build](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)
- [100. Gradle 9.9.1: plugin Application, ejecución y distribución](https://docs.gradle.org/current/userguide/application_plugin.html)
- [101. Apache Maven Compiler Plugin: compilar contra una versión Java con release](https://maven.apache.org/plugins/maven-compiler-plugin/examples/set-compiler-release.html)
- [104. Apache Maven Compiler Plugin: versión y documentación](https://maven.apache.org/plugins/maven-compiler-plugin)
- [190. Apache Maven: instalación y requisitos](https://maven.apache.org/install.html)
- [191. Gradle: instalación y prerrequisitos](https://docs.gradle.org/current/userguide/installation.html)
- [208. Apache Maven: Introduction to the Dependency Mechanism](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html)
- [209. Sonatype Central Repository Coordinates](https://central.sonatype.org/publish/requirements/coordinates)
- [210. Apache Maven Releases History](https://maven.apache.org/docs/history.html)
- [211. Gradle Compatibility Matrix](https://docs.gradle.org/current/userguide/compatibility.html)
- [232. Guía oficial de Maven para fijar la versión Java objetivo](https://maven.apache.org/guides/mini/guide-java-target.html)

### 25.9. Pruebas automatizadas y calidad del software

- [102. JUnit 6.1.3 User Guide: componentes y requisitos de Java](https://docs.junit.org/6.1.3/overview.html)
- [103. Maven Central: artefacto JUnit Jupiter 6.1.3](https://repo.maven.apache.org/maven2/org/junit/jupiter/junit-jupiter/6.1.3)
- [105. Apache Maven Surefire Plugin 3.6.1: ejecución de pruebas JUnit](https://maven.apache.org/surefire/maven-surefire-plugin/examples/junit.html)
- [153. Documentación IntelliJ IDEA: depuración de código](https://www.jetbrains.com/help/idea/debugging-code.html)
- [154. Documentación Visual Studio Code: depuración Java](https://code.visualstudio.com/docs/java/java-debugging)
- [195. JUnit Jupiter: anotaciones de prueba y ciclo de vida](https://docs.junit.org/6.1.3/writing-tests/annotations.html)
- [196. JUnit Jupiter: assertions](https://docs.junit.org/6.1.3/writing-tests/assertions.html)
- [197. JUnit Jupiter: pruebas parametrizadas](https://docs.junit.org/6.1.3/writing-tests/parameterized-classes-and-tests.html)
- [199. JUnit 6: integración con Maven y Gradle](https://docs.junit.org/6.1.3/running-tests/build-support.html)
- [200. Apache Maven Surefire: uso de JUnit Platform](https://maven.apache.org/surefire/maven-surefire-plugin/examples/junit-platform.html)
- [201. Gradle User Manual: pruebas en proyectos Java y JVM](https://docs.gradle.org/current/userguide/java_testing.html)
- [202. Mockito: repositorio y documentación del proyecto](https://github.com/mockito/mockito)
- [203. Mockito JUnit Jupiter Extension](https://javadoc.io/doc/org.mockito/mockito-junit-jupiter/5.23.0/org/mockito/junit/jupiter/MockitoExtension.html)
- [204. JaCoCo: Maven Plugin](https://www.eclemma.org/jacoco/trunk/doc/maven.html)
- [205. JaCoCo: métricas y contadores de cobertura](https://www.eclemma.org/jacoco/trunk/doc/counters.html)
- [206. JaCoCo: historial de cambios y compatibilidad de bytecode](https://www.jacoco.org/jacoco/trunk/doc/changes.html)
- [223. Documentación de SpotBugs](https://spotbugs.github.io/)
- [224. Instalación oficial de Error Prone](https://errorprone.info/docs/installation)
- [225. Documentación oficial de Checkstyle](https://checkstyle.org/)
- [226. Uso del complemento Checkstyle para Maven](https://maven.apache.org/plugins/maven-checkstyle-plugin/usage.html)
- [227. Uso del complemento SpotBugs para Maven](https://spotbugs.readthedocs.io/en/latest/maven.html)
- [228. Opciones y configuración de Error Prone](https://errorprone.info/docs/flags)
- [230. Guía oficial de usuario de JUnit](https://docs.junit.org/current/user-guide/)
- [231. Artefacto JUnit Jupiter en Maven Central](https://central.sonatype.com/artifact/org.junit.jupiter/junit-jupiter)

### 25.10. Entrada, salida y manejo de archivos

- [108. Java SE 25 API: InputStream](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/io/InputStream.html)
- [109. Java SE 25 API: Reader](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/io/Reader.html)
- [110. Java SE 25 API: BufferedReader](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/io/BufferedReader.html)
- [111. Java SE 25 API: Console](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/io/Console.html)
- [112. Java SE 25 API: Scanner](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/Scanner.html)
- [113. Java SE 25 API: InputStreamReader y charset](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/io/InputStreamReader.html)
- [114. Java SE 25 API: PrintStream](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/io/PrintStream.html)
- [115. JEP 400: UTF-8 by Default](https://openjdk.org/jeps/400)
- [116. Java SE 25 API: Files](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/nio/file/Files.html)
- [117. Java SE 25 API: Path](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/nio/file/Path.html)
- [119. Java SE 25 API: AutoCloseable](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/lang/AutoCloseable.html)

### 25.11. JSON, XML, CSV y serialización

- [120. RFC 8259: The JavaScript Object Notation JSON Data Interchange Format](https://www.rfc-editor.org/rfc/rfc8259)
- [121. W3C XML Recommendation](https://www.w3.org/TR/xml)
- [122. Maven Central: Jackson Databind](https://central.sonatype.com/artifact/com.fasterxml.jackson.core/jackson-databind)
- [123. Gson User Guide](https://google.github.io/gson/UserGuide.html)
- [124. FasterXML Jackson documentation hub](https://github.com/FasterXML/jackson-docs)
- [126. JEP 540: Simple JSON API incubadora](https://openjdk.org/jeps/540)
- [127. Java SE 25 JAXP Security Guide](https://docs.oracle.com/en/java/javase/25/security/java-api-xml-processing-jaxp-security-guide.html)
- [128. RFC 4180: Common Format and MIME Type for CSV Files](https://www.rfc-editor.org/rfc/rfc4180)
- [129. Apache Commons CSV API y guía de usuario](https://commons.apache.org/proper/commons-csv/apidocs/index.html)
- [130. Maven Central: Apache Commons CSV](https://central.sonatype.com/artifact/org.apache.commons/commons-csv)
- [131. Java SE 27 API: Serializable](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/io/Serializable.html)
- [133. Oracle Java SE 25: Addressing Deserialization Vulnerabilities](https://docs.oracle.com/en/java/javase/25/core/addressing-serialization-vulnerabilities.html)
- [134. JEP 154: Remove Serialization, propuesta retirada](https://openjdk.org/jeps/154)
- [135. JEP 290: Filter Incoming Serialization Data](https://openjdk.org/jeps/290)

### 25.12. Concurrencia, paralelismo y programación asíncrona

- [85. API Java SE 25: utilidades de concurrencia](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/concurrent/package-summary.html)
- [86. JEP 444: Virtual Threads](https://openjdk.org/jeps/444)
- [87. JEP 533: Structured Concurrency, Seventh Preview](https://openjdk.org/jeps/533)
- [136. Paquete java.util.concurrent de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/concurrent/package-summary.html)
- [137. API Thread de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/lang/Thread.html)
- [138. API CompletableFuture de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/concurrent/CompletableFuture.html)
- [139. API ExecutorService de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/concurrent/ExecutorService.html)
- [141. API Future de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/concurrent/Future.html)
- [142. JEP 491: Synchronize Virtual Threads without Pinning](https://openjdk.org/jeps/491)
- [144. JEP 12: Preview Language and VM Features](https://openjdk.org/jeps/12)
- [145. Paquete de bloqueos y condiciones de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/concurrent/locks/package-summary.html)
- [146. Paquete java.util.concurrent.atomic de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/concurrent/atomic/package-summary.html)
- [147. API ConcurrentHashMap de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/concurrent/ConcurrentHashMap.html)
- [150. API ForkJoinPool de Java SE 27](https://docs.oracle.com/en/java/javase/27/docs/api/java.base/java/util/concurrent/ForkJoinPool.html)

### 25.13. Manejo de excepciones, depuración y logging

- [151. Tutorial Oracle: captura y tratamiento de excepciones](https://docs.oracle.com/javase/tutorial/essential/exceptions/handling.html)
- [152. Tutorial Oracle: try con recursos y excepciones suprimidas](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html)
- [156. API Java SE 27: paquete java.util.logging](https://docs.oracle.com/en/java/javase/27/docs/api/java.logging/java/util/logging/package-summary.html)
- [157. Manual oficial de SLF4J](https://www.slf4j.org/manual.html)
- [158. Manual oficial de Logback](https://logback.qos.ch/manual)
- [159. Manual oficial de Apache Log4j 2](https://logging.apache.org/log4j/2.x/manual/index.html)
- [160. Maven Central: artefacto slf4j-api](https://central.sonatype.com/artifact/org.slf4j/slf4j-api)
- [161. Maven Central: artefacto logback-classic](https://central.sonatype.com/artifact/ch.qos.logback/logback-classic)

### 25.14. Seguridad y buenas prácticas

- [162. Secure Coding Guidelines for Java SE](https://www.oracle.com/java/technologies/javase/seccodeguide.html)
- [163. Java SE 25 Security Developer’s Guide](https://docs.oracle.com/en/java/javase/25/security/java-security-overview1.html)
- [164. OWASP Input Validation Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)
- [165. Java SE 25 PreparedStatement API](https://docs.oracle.com/en/java/javase/25/docs/api/java.sql/java/sql/PreparedStatement.html)
- [166. OWASP SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
- [167. OWASP Java Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Java_Security_Cheat_Sheet.html)
- [168. OWASP Cross Site Scripting Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
- [169. OWASP Java Encoder Project](https://owasp.org/www-project-java-encoder)
- [170. OWASP Java Encoder 1.6.0 on Maven Central](https://central.sonatype.com/artifact/org.owasp.encoder/1.6.0)
- [171. OWASP Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)
- [172. Spring Security Password Storage](https://docs.spring.io/spring-security/reference/features/authentication/password-storage.html)
- [173. Java SE 25 SecureRandom API](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/security/SecureRandom.html)
- [174. Java SE 25 Cipher API](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/javax/crypto/Cipher.html)
- [175. OWASP Transport Layer Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Security_Cheat_Sheet.html)
- [176. JEP 486: Permanently Disable the Security Manager](https://openjdk.org/jeps/486)
- [177. OWASP Software Supply Chain Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Software_Supply_Chain_Security_Cheat_Sheet.html)

### 25.15. Instalación, configuración y distribución de Java

- [178. IntelliJ IDEA: JDK y SDK de proyecto](https://www.jetbrains.com/help/idea/sdk.html)
- [180. Oracle Java SE: resumen de instalación del JDK](https://docs.oracle.com/en/java/javase/26/install/overview-jdk-installation.html)
- [184. Licencia OpenJDK GPLv2 con Classpath Exception](https://openjdk.org/legal/gplv2+ce.html)
- [185. Oracle No-Fee Terms and Conditions License](https://www.oracle.com/downloads/licenses/no-fee-license.html)
- [186. Eclipse Adoptium: misión, TCK y licencias](https://adoptium.net/about)
- [187. Eclipse Temurin: instalación de paquetes MSI en Windows](https://adoptium.net/installation/windows)
- [188. Eclipse Temurin: instalación de paquetes PKG en macOS](https://adoptium.net/installation/macOS)
- [189. Eclipse Temurin: paquetes RPM, DEB y APK para Linux](https://adoptium.net/installation/linux)
- [217. Eclipse Adoptium: soporte y calendario de versiones Temurin](https://adoptium.net/support)

### 25.16. IDE, frameworks y ecosistema Java

- [194. Visual Studio Code: documentación de Java](https://code.visualstudio.com/docs/languages/java)
- [212. Spring Boot System Requirements](https://docs.spring.io/spring-boot/system-requirements.html)
- [213. Jakarta EE Platform 11](https://jakarta.ee/specifications/platform/11)
- [214. Quarkus 3.40 LTS release announcement](https://quarkus.io/blog/quarkus-3-40-released)
- [215. Micronaut Framework 5.0.0 GA and Java 25 baseline](https://micronaut.io/2026/05/20/micronaut-framework-5-0-0-released)
- [216. Micronaut Framework 5.2.6 security release](https://micronaut.io/2026/11/11/micronaut-framework-5-2-6)

### 25.17. Recursos complementarios

- [7. Java SE 25 API: catálogo oficial de clases y módulos](https://docs.oracle.com/en/java/javase/25/docs/api/index.html)
- [94. Oracle Java SE 27 API Specification](https://docs.oracle.com/en/java/javase/27/docs/api/index.html)
- [207. Dev.java: The Core JDK Tools](https://dev.java/learn/jvm/core-tools)