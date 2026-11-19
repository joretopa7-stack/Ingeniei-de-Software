![Logotipo oficial de Python](https://www.python.org/static/community_logos/python-logo.png)

# Guía completa de Python

**Versión objetivo:** CPython 3.15.2  
**Fecha de referencia:** 18 de noviembre de 2026  
**Nivel:** progresivo, desde principiante hasta avanzado  
**Propósito:** material de estudio y consulta técnica para construir, probar y mantener programas Python.

> La página oficial de descargas identifica Python 3.15.2, publicada el 25 de octubre de 2026, como versión estable vigente al corte de esta guía; Python 3.16 aún se encuentra en desarrollo. Si consultas esta guía después de la fecha de referencia, vuelve a comprobar la página de versiones y la tabla de soporte antes de instalar o fijar una versión [1] [2]. La imagen enlazada es el logotipo oficial publicado en python.org; al ser un recurso remoto, su visualización depende de que GitHub o el visor pueda acceder a esa URL.

## Índice

1. [Fundamentos y características de Python](#1-fundamentos-y-características-de-python)
2. [Sintaxis y semántica](#2-sintaxis-y-semántica)
3. [Tipos de datos y sistema de tipos](#3-tipos-de-datos-y-sistema-de-tipos)
4. [Fundamentos de programación](#4-fundamentos-de-programación)
5. [Estructuras de datos](#5-estructuras-de-datos)
6. [Paradigmas de programación](#6-paradigmas-de-programación)
7. [Modularidad y organización del código](#7-modularidad-y-organización-del-código)
8. [Memoria, objetos y gestión de recursos](#8-memoria-objetos-y-gestión-de-recursos)
9. [Entrada, salida y serialización](#9-entrada-salida-y-serialización)
10. [Concurrencia y paralelismo](#10-concurrencia-y-paralelismo)
11. [Errores, excepciones y depuración](#11-errores-excepciones-y-depuración)
12. [Seguridad](#12-seguridad)
13. [Herramientas, instalación y ciclo de desarrollo](#13-herramientas-instalación-y-ciclo-de-desarrollo)
14. [Pruebas de software](#14-pruebas-de-software)
15. [Ecosistema, biblioteca estándar y paquetes](#15-ecosistema-biblioteca-estándar-y-paquetes)
16. [Buenas prácticas y calidad del código](#16-buenas-prácticas-y-calidad-del-código)
17. [Aplicabilidad entre lenguajes](#17-aplicabilidad-entre-lenguajes)
18. [Cómo estudiar y utilizar esta guía](#18-cómo-estudiar-y-utilizar-esta-guía)
19. [Referencia rápida](#19-referencia-rápida)
20. [Errores típicos de principiantes](#20-errores-típicos-de-principiantes)
21. [Ejercicios progresivos](#21-ejercicios-progresivos)
22. [Soluciones de los ejercicios](#22-soluciones-de-los-ejercicios)
23. [Mini proyectos](#23-mini-proyectos)
24. [Glosario](#24-glosario)
25. [Documentación y fuentes oficiales](#25-documentación-y-fuentes-oficiales)
26. [References](#references)

## 1. Fundamentos y características de Python

### Qué es y para qué sirve

Python es un lenguaje de programación de alto nivel y propósito general. Sus abstracciones —cadenas, colecciones, excepciones, módulos— permiten expresar operaciones sin administrar cada detalle de la máquina. Es dinámico: los objetos tienen tipos y los nombres pueden vincularse a objetos de tipos distintos durante la ejecución. Python admite estilos imperativos, procedimentales, orientados a objetos y funcionales, entre otros; no obliga a escoger uno para todo el programa [3].

Python es el lenguaje; **CPython** es su implementación más extendida y de referencia. En CPython el código fuente normalmente se compila a bytecode que ejecuta una máquina virtual. No debe suponerse que todas las implementaciones internas, características de rendimiento o extensiones nativas sean idénticas. La portabilidad depende también de las bibliotecas y plataformas disponibles [3] [4].

Python es software abierto bajo licencia de la Python Software Foundation (PSF), utilizable en proyectos comerciales conforme a sus condiciones. Las dependencias externas tienen sus propias licencias y obligaciones [5].

### Historia en síntesis

Guido van Rossum comenzó Python durante las vacaciones de Navidad de 1989 en CWI, Países Bajos, como herramienta extensible para tareas de sistemas en el entorno Amoeba. La primera publicación pública se hizo en 1991. El lenguaje tomó ideas de ABC, entre ellas legibilidad e indentación significativa, y de Modula-3 para aspectos de excepciones. Su nombre alude al programa británico *Monty Python’s Flying Circus*, no a la serpiente [3].

Python 2.0 apareció en 2000; Python 3.0 se publicó el 3 de diciembre de 2008 con incompatibilidades deliberadas respecto de 2.x. El soporte de Python 2 finalizó el 1 de enero de 2020, por lo que no es una base apropiada para nuevos desarrollos mantenidos [3] [6]. Desde Python 3.9 se planifica una versión anual de nuevas características, normalmente en octubre. Cada rama pasa por etapas de desarrollo y mantenimiento; el calendario oficial puede cambiar [7] [2].

### Características, fortalezas y límites

Sus características destacadas son sintaxis legible, indentación significativa, modo interactivo, módulos, excepciones, biblioteca estándar amplia e integración con código de otros lenguajes. Se usa en automatización, educación, servicios web, ciencia, análisis de datos, redes, herramientas internas, software empresarial y videojuegos [3] [8].

| Fortalezas | Consideraciones y límites |
|---|---|
| Ciclo de edición y prueba rápido; abundante material didáctico. | Tipado dinámico: ciertos errores aparecen solo en rutas ejecutadas; pruebas y análisis estático son importantes. |
| Multiparadigma, modular y con amplia biblioteca estándar y ecosistema. | La compatibilidad de paquetes, plataformas y versiones debe comprobarse. |
| Adecuado para automatización, servicios, análisis y prototipos. | Bucles Python puros no suelen ser la primera opción para control de hardware de bajo nivel o restricciones estrictas de tiempo y memoria. |
| Puede integrarse con extensiones nativas y bibliotecas optimizadas. | El rendimiento depende de la carga, implementación, dependencias y plataforma; perfilar antes de optimizar. |

No es correcto afirmar que Python “siempre es lento”: operaciones numéricas pueden delegarse a bibliotecas con componentes nativos. La elección debe atender requisitos medibles, soporte, despliegue e interoperabilidad, no solo popularidad. Para un sistema nuevo al corte de esta guía, la referencia es **CPython 3.15.2**, siempre que dependencias y plataformas lo soporten; un proyecto de producción puede fijar otra rama soportada por compatibilidad [1] [2].

## 2. Sintaxis y semántica

La **sintaxis** define las formas de código aceptadas por la gramática. La **semántica** describe su significado y comportamiento. Un programa puede ser sintácticamente válido y aun así producir una excepción o un resultado contrario al requisito [9] [10].

### Bloques, indentación y sentencias

Las cabeceras de sentencias compuestas (`if`, `for`, `while`, `def`, `class`, `try`, `with`, `match`) terminan con `:`. El bloque se delimita mediante sangría; esta es sintaxis, no decoración. PEP 8 recomienda cuatro espacios por nivel y no mezclar tabuladores con espacios [11] [12].

```python
temperatura = 22
if temperatura > 20:
    print("Hace calor")
    print("Usa ropa ligera")
print("Fin")
```

Salida esperada:

```text
Hace calor
Usa ropa ligera
Fin
```

Una expresión produce un valor (`2 + 3`); una sentencia realiza una acción (`total = 2 + 3`). En un archivo, escribir solo `total` no muestra automáticamente su valor; la presentación automática corresponde al modo interactivo. Paréntesis, corchetes y llaves permiten continuar una expresión en varias líneas; es preferible a una barra inversa final [9] [10].

### Identificadores, palabras clave y mayúsculas

Los identificadores ASCII empiezan por una letra o `_`, y pueden contener dígitos después: `resultado_2` es válido; `2resultado` no. Python 3 también admite identificadores Unicode que satisfacen las reglas Unicode, normalizados a NFKC; para APIs compartidas, los nombres ASCII suelen ser más fáciles de revisar [9]. Python distingue mayúsculas: `cliente`, `Cliente` y `CLIENTE` son tres nombres diferentes.

Palabras reservadas incluyen `False`, `None`, `True`, `and`, `as`, `async`, `await`, `break`, `class`, `def`, `else`, `for`, `from`, `if`, `import`, `in`, `is`, `lambda`, `not`, `or`, `pass`, `return`, `try`, `while`, `with` y `yield`. Algunas son **palabras clave suaves**: `match`, `case`, `_` y `type` tienen uso contextual; en Python 3.15, `lazy` es palabra clave suave antes de una sentencia `import`. No asumas ese comportamiento al escribir código para versiones previas [9].

### Comentarios, docstrings y errores

Un comentario comienza con `#` fuera de una cadena. Las cadenas triples no son comentarios; si una cadena aparece como primera instrucción de un módulo, clase o función, es su *docstring*. Comentarios útiles explican intención o restricciones no obvias, no repiten literalmente la línea siguiente [11] [13].

Errores sintácticos suelen producir `SyntaxError`; problemas de indentación, `IndentationError` o `TabError`. Las excepciones de ejecución incluyen `NameError`, `TypeError` y `ZeroDivisionError`. Un error lógico —por ejemplo, sumar cuando el requisito era restar— puede no generar excepción y debe detectarse mediante razonamiento y pruebas [10] [14].

```python
# Incorrecto: falta ':'
# if edad >= 18
#     print("Acceso")

# Correcto
edad = 20
if edad >= 18:
    print("Acceso permitido")
```

## 3. Tipos de datos y sistema de tipos

En Python todo dato es un **objeto**, con identidad, tipo y valor. Los nombres se enlazan a objetos; no son contenedores tipados de forma permanente. `type(x)` consulta el tipo concreto; `isinstance(x, T)` suele ser mejor para aceptar una clase y sus subclases [15] [16].

### Tipado dinámico, anotaciones e inferencia

Python es dinámicamente tipado: los tipos se determinan durante la ejecución. A menudo se denomina fuertemente tipado porque no convierte silenciosamente cualquier combinación; pero “fuerte” y “débil” carecen de una escala universal precisa. Explica las reglas concretas: `4 + 0.5` funciona por promoción numérica; `"4" + 0.5` produce `TypeError` [16].

Las anotaciones (`def total(items: list[int]) -> int`) documentan contratos y ayudan a IDEs y comprobadores estáticos, pero el intérprete no las aplica como validación automática. `Any` relaja el análisis; `object` es más restrictivo y exige comprobar antes de usar operaciones específicas. La inferencia de tipos y los diagnósticos dependen de la herramienta y su configuración [17] [18]. Desde 3.9 se parametrizan colecciones incorporadas (`list[int]`); desde 3.10 se escriben uniones como `int | str`; desde 3.12 existen parámetros de tipo nativos (`def primero[T](...)`). Python 3.14 difirió por defecto la evaluación de anotaciones, lo que importa en introspección [17].

```python
def etiqueta(codigo: int) -> str:
    return f"código={codigo}"

print(etiqueta("X7"))  # La anotación no rechaza la llamada en ejecución.
```

Salida esperada: `código=X7`. Un analizador estático configurado sí puede señalar el argumento incompatible.

### Tipos incorporados más usados

| Familia | Tipos | Uso y matices |
|---|---|---|
| Números | `int`, `float`, `complex`, `bool` | `int` tiene precisión arbitraria limitada por memoria; `float` es aproximado; `bool` es subclase de `int`. `Decimal` y `Fraction` son tipos de módulos estándar. |
| Texto/binario | `str`, `bytes`, `bytearray`, `memoryview` | `str` es Unicode e inmutable; `bytes` inmutable; `bytearray` mutable. Codificar/decodificar es explícito. |
| Secuencias | `list`, `tuple`, `range` | Listas mutables; tuplas inmutables respecto a sus referencias; `range` representa progresiones sin materializar lista. |
| Mapeo | `dict` | Claves hashables, valores de cualquier tipo; orden de inserción garantizado desde 3.7. |
| Conjuntos | `set`, `frozenset` | Elementos únicos hashables; el primero mutable, el segundo inmutable y hashable. No prometen orden. |
| Ausencia | `None` | Singleton distinto de `False`, `0` y cadena vacía; comprobar con `is None`. |

`bool` puede comportarse como `0` y `1`; `True == 1` es verdadero, pero `True is 1` es falso. La igualdad (`==`) compara valor; la identidad (`is`) pregunta si es el mismo objeto. Usa `is` para `None`, no para comparar enteros o cadenas [16].

Mutabilidad pertenece al objeto: listas, diccionarios, conjuntos y `bytearray` se pueden cambiar; números, cadenas, bytes y tuplas no. Una tupla puede contener una lista mutable. `b = a` crea un alias, no una copia; `a.copy()` es copia superficial. Los objetos hashables mantienen un hash estable y una relación coherente con igualdad; esto permite usarlos como claves de diccionario o elementos de conjunto [15] [16].

```python
original = [1, 2]
alias = original
copia = original.copy()
alias.append(3)
print(original, copia)
```

Salida esperada: `[1, 2, 3] [1, 2]`.

En condiciones, colecciones vacías, cero, `False` y `None` son falsy; la mayoría de objetos no vacíos son truthy. `and` y `or` pueden devolver uno de sus operandos, no necesariamente un booleano. Conversión explícita mediante `int()`, `float()`, `str()`, `encode()` y `decode()` debe ajustarse al dato: `bool("False")` da `True`; `int(-3.8)` trunca hacia cero [16].

## 4. Fundamentos de programación

### Nombres, asignación y constantes

La asignación vincula un nombre a un objeto; reasignar no convierte el objeto anterior. El desempaquetado asigna varios nombres (`x, y = punto`), y el intercambio `x, y = y, x` no requiere variable temporal. Python no impone constantes generales: `MAX_INTENTOS = 3` es convención; `typing.Final` puede informar al comprobador, no impedir reasignación en tiempo de ejecución [10] [17]. Evita ocultar incorporados como `list`, `str` o `sum` con nombres de variables.

### Operadores y expresiones

Aritméticos: `+`, `-`, `*`, `/`, `//`, `%`, `**`. `/` es división verdadera; `//` es división de piso, por lo que `-7 // 3 == -3`. Comparación: `<`, `<=`, `>`, `>=`, `==`, `!=`; pertenencia `in`, `not in`; identidad `is`, `is not`; lógicos `and`, `or`, `not`. `&`, `|`, `^`, `~`, `<<`, `>>` son bit a bit, no reemplazos de operadores lógicos. Usa paréntesis si mejoran la lectura [10] [16].

```python
subtotal = 4 * 7 + 2
con_descuento = subtotal * (1 - 0.10)
print(subtotal, round(con_descuento, 2))
print(17 // 5, 17 % 5, 2 ** 5)
```

Salida esperada:

```text
30 27.0
3 2 32
```

### Condicionales y bucles

`if`/`elif`/`else` seleccionan ramas; solo se ejecuta la primera condición verdadera. `for` recorre elementos de un iterable; `range(inicio, fin, paso)` excluye el límite final. `enumerate()` es preferible a `range(len(...))` cuando se necesitan índice y valor. `while` repite mientras una condición sea verdadera. `break` sale del bucle más interno; `continue` pasa a la siguiente iteración. El `else` de un bucle se ejecuta si terminó sin `break` [19].

```python
frutas = ["pera", "kiwi", "mango"]
for indice, fruta in enumerate(frutas, start=1):
    print(f"{indice}: {fruta}")
```

Salida esperada: `1: pera`, `2: kiwi`, `3: mango`, cada una en su línea.

### Funciones, parámetros y ámbito

`def` crea una función; el cuerpo corre al llamarla. Parámetros son nombres de la definición; argumentos son valores de la llamada. Sin `return`, la función devuelve `None`. Python admite argumentos posicionales y nombrados; `/` marca parámetros solo posicionales y `*` los solo nombrados. `*args` reúne argumentos posicionales extra en tupla; `**kwargs`, los nombrados en diccionario [19].

```python
def calcular_total(precio, cantidad=1):
    """Calcula un total antes de impuestos."""
    return precio * cantidad

print(calcular_total(2.5, cantidad=4))
```

Salida esperada: `10.0`. Mantén cálculo separado de entrada/salida cuando ayude a probar y reutilizar la función.

Los valores predeterminados se evalúan al definir la función. Evita listas mutables como valores predeterminados: usa `None` y crea una nueva lista dentro. Los parámetros reciben referencias a los mismos objetos; mutar una lista recibida afecta al objeto del llamador, pero reasignar el parámetro no reasigna el nombre del llamador [19].

El recordatorio LEGB significa búsqueda de nombres en ámbitos local, envolvente, global y built-in. Una asignación dentro de una función hace local ese nombre salvo `global` o `nonlocal`. Las funciones anidadas pueden conservar enlaces a variables externas en cierres. Prefiere pasar argumentos explícitos frente a estado global oculto [20].

### Comprensiones, recursión y algoritmos

Las comprensiones crean listas, conjuntos o diccionarios a partir de iterables y filtros. Para una transformación sencilla son expresivas; para lógica compleja, efectos secundarios o anidación profunda, usa un bucle. Los generadores `(expresión for elemento in iterable)` producen valores de forma perezosa [21].

```python
cuadrados_pares = [n**2 for n in range(1, 8) if n % 2 == 0]
print(cuadrados_pares)
```

Salida esperada: `[4, 16, 36]`.

Una función recursiva se llama a sí misma; necesita caso base y reducción hacia él. Para una profundidad potencialmente grande, un bucle suele evitar consumir pila de llamadas. No dependas de optimización de llamadas de cola [20].

Un algoritmo es un procedimiento finito para resolver un problema. La complejidad temporal y espacial describe cómo crece el trabajo o la memoria según el tamaño de entrada. Notación Big O expresa crecimiento asintótico, no segundos reales: `O(1)` constante, `O(log n)` logarítmica, `O(n)` lineal, `O(n log n)` frecuente en ordenación eficiente, `O(n²)` cuadrática. Las cifras de listas, diccionarios y conjuntos aquí son las documentadas para CPython y pueden no ser garantía de otras implementaciones [22].

```python
def contiene_duplicados(valores):
    vistos = set()
    for valor in valores:
        if valor in vistos:
            return True
        vistos.add(valor)
    return False

print(contiene_duplicados([3, 8, 3]))
```

Salida esperada: `True`. En promedio, la versión con `set` puede reducir una búsqueda repetida de O(n²) a O(n), a costa de O(n) memoria; los elementos deben ser hashables y las operaciones hash no tienen garantía de O(1) en el peor caso [22].

## 5. Estructuras de datos

La selección debe reflejar las operaciones dominantes. Las complejidades de tipos integrados indicadas son orientativas para CPython [22].

| Estructura | Python | Uso y coste orientativo |
|---|---|---|
| Lista/array dinámico | `list` integrada | Secuencia ordenada, mutable, indexación O(1), búsqueda O(n), `append` O(1) amortizado; insertar al inicio O(n). |
| Tupla | `tuple` integrada | Grupo ordenado inmutable; índice O(1), búsqueda O(n). |
| Mapa/hash | `dict` integrada | Asociación clave-valor; consulta promedio O(1), peor caso O(n); orden de inserción garantizado. |
| Conjunto/hash | `set`, `frozenset` | Unicidad y pertenencia, promedio O(1); sin orden ni indexación posicional. |
| Pila | `list` | `append()` y `pop()` al final, LIFO, O(1) amortizado. |
| Cola | `collections.deque` estándar | FIFO con `append()` y `popleft()` aproximadamente O(1); no uses `list.pop(0)` como cola. |
| Prioridad | `heapq` estándar | Min-heap; raíz mínima, `heappush`/`heappop` O(log n), `heapify` O(n); no mantiene toda la lista ordenada. |
| Array homogéneo | `array.array` estándar | Valores de tipo C homogéneo y compacto; tamaño depende de plataforma. No sustituye a NumPy para cálculo vectorizado. |
| Lista enlazada | No integrada como tipo general | Puede implementarse con nodos, pero `list` o `deque` suelen ser preferibles; insertar al inicio O(1), buscar O(n). |
| Árbol | No integrado como estructura general | BST no balanceado puede degradar de O(log n) a O(n); clase didáctica no es estructura de producción balanceada. |
| Grafo | No integrado como tipo dedicado | Diccionario de adyacencia basta en casos simples; BFS con lista de adyacencia O(V+E). NetworkX es tercero [23]. |

`{}` crea un diccionario vacío; `set()` crea un conjunto vacío. Tupla de un elemento: `(7,)`. Una tupla solo es hashable si todos sus miembros lo son. Un error de alias común es `matriz = [[0] * 3] * 2`, que repite referencias a la misma fila; crear con `[[0] * 3 for _ in range(2)]` genera filas independientes [16] [21] [24].

## 6. Paradigmas de programación

Paradigmas describen formas de razonar; pueden combinarse. Imperativo expresa pasos y cambios de estado; procedimental organiza esos pasos en funciones; estructurado usa secuencia, selección y repetición. Python ofrece `if`, `for`, `while` y `def` como mecanismos habituales [19].

La programación orientada a objetos organiza estado y comportamiento en clases e instancias. Python permite herencia simple y múltiple, sobrescritura y despacho dinámico, pero no requiere clases para toda solución. Guion bajo inicial es convención de uso interno, no privacidad estricta [25].

```python
class Pedido:
    def __init__(self, unidades, precio):
        self.unidades = unidades
        self.precio = precio

    def subtotal(self):
        return self.unidades * self.precio

print(Pedido(3, 12.5).subtotal())
```

Salida esperada: `37.5`.

El estilo funcional favorece funciones componibles, transformaciones y pocos efectos secundarios. Funciones, `lambda`, generadores y comprensiones son capacidades del lenguaje; `itertools` y `functools` son módulos estándar. Python no es funcional puro: admite mutación e I/O. SQL es un ejemplo declarativo; una comprensión Python es concisa, pero especifica el recorrido y filtro y no equivale a un lenguaje declarativo puro [3] [21].

La programación reactiva procesa flujos de eventos; Python no trae un framework general de observables integrado. RxPY (`reactivex`) es tercero. Concurrencia coordina tareas solapadas, no es un paradigma de organización único; se trata en la sección 10 [26].

## 7. Modularidad y organización del código

Un **módulo** suele ser un archivo `.py` importable; un **paquete** organiza módulos bajo un nombre con puntos. Al importar se ejecuta el código de nivel superior la primera vez y el módulo se conserva en `sys.modules`; por ello, evita efectos secundarios sustanciales al importar [27].

```text
analizador/
├── pyproject.toml
├── README.md
├── src/
│   └── analizador_texto/
│       ├── __init__.py
│       ├── __main__.py
│       ├── cli.py
│       └── conteo.py
└── tests/
    └── test_conteo.py
```

`src/` contiene el paquete importable, `tests/` las pruebas, `pyproject.toml` metadatos y configuración. Para una biblioteca distribuible, el diseño `src/` ayuda a comprobar que se importa el paquete instalado y no accidentalmente el directorio de trabajo [28].

Formas típicas: `import pathlib`, `from pathlib import Path`, `import pathlib as pl`, `from . import modelos`. Los imports relativos requieren contexto de paquete; ejecuta el módulo como `python -m paquete.modulo`. Evita `from modulo import *` en código mantenido y ordena imports en biblioteca estándar, terceros y código propio [11] [27].

`__init__.py` se ejecuta al importar un paquete regular y puede estar vacío; `__all__` documenta ciertos exports, no es mecanismo de seguridad. Paquetes de espacio de nombres sin `__init__.py` permiten distribuir partes de un namespace, pero solo deben usarse deliberadamente [27] [29].

```python
# mi_paquete/saludo.py

def main() -> int:
    print("Hola")
    return 0

if __name__ == "__main__":
    raise SystemExit(main())
```

El guardián `__main__` permite ejecutar el módulo sin activar la aplicación al importarlo. Para publicar, `pyproject.toml` distingue `[build-system]`, `[project]` y `[tool.*]`; un backend construye un sdist y/o wheel. PyPA documenta el proceso actual; no se necesita `setup.py` para proyectos modernos sencillos [28] [30].

## 8. Memoria, objetos y gestión de recursos

Un nombre y un contenedor mantienen referencias a objetos; asignar `b = a` no copia. `del a` elimina un enlace, no ordena necesariamente destruir el objeto. `==` compara igualdad por valor; `is` identidad. `id()` es único durante la vida del objeto, pero no es una dirección portable; en CPython se corresponde actualmente con una dirección, detalle de implementación [15] [20].

Python no exige administrar manualmente la memoria de cada objeto ni garantiza una ubicación simple de variables en *stack* y objetos en *heap*. En CPython, el conteo de referencias suele liberar objetos cuando no hay referencias fuertes, complementado por un recolector de ciclos. El momento de destrucción no es garantía del lenguaje; otras implementaciones pueden gestionar memoria de otro modo. No uses `__del__` ni el recolector como mecanismo para cerrar archivos o sockets [15] [31].

El `with` administra recursos con limpieza al salir, incluso ante excepciones. Úsalo para archivos, conexiones o bloqueos que ofrezcan gestor de contexto; si no, `try/finally` asegura limpieza [12].

```python
with open("datos.txt", "w", encoding="utf-8") as archivo:
    archivo.write("contenido\n")
print(archivo.closed)
```

Salida esperada: `True`. Los objetos gestionados por `with` no equivalen a punteros explícitos ni a un modelo de ownership/borrowing como Rust; en la C API de extensiones sí hay reglas de referencias propias [33].

## 9. Entrada, salida y serialización

`input()` devuelve siempre `str`; la conversión y validación son explícitas. `print()` permite `sep`, `end`, `file` y `flush`; `sys.stdout` suele ser salida normal y `sys.stderr` diagnóstico [34].

### Archivos, rutas y codificaciones

Usa `pathlib.Path` para representar rutas portables. Las rutas relativas se interpretan respecto del directorio de trabajo del proceso, no necesariamente respecto del archivo Python. `open()` en modo texto procesa `str`; modo binario (`rb`, `wb`) procesa bytes. `w` trunca; `x` crea solo si no existe; `a` añade; `r` lee. Usa `with` y declara `encoding="utf-8"` en archivos de texto intercambiables. Python 3.15 activa UTF-8 Mode por defecto, pero declarar codificación explicita el contrato y facilita compatibilidad [34] [35] [36].

```python
from pathlib import Path

ruta = Path("notas.txt")
ruta.write_text("Primera línea\n", encoding="utf-8")
with ruta.open(encoding="utf-8") as archivo:
    print(archivo.read(), end="")
```

Las rutas que provienen de usuarios requieren validación de contención; `resolve()` e `is_relative_to()` ayudan frente a escapes sencillos, pero no eliminan carreras si un atacante puede modificar el árbol de directorios [35].

### JSON, CSV y XML

La biblioteca estándar tiene módulos `json`, `csv` y `xml.etree.ElementTree`. JSON traduce objetos JSON a tipos como `dict`, `list`, `str`, números, `bool` y `None`; la carga correcta no valida el esquema de negocio. JSON no es un protocolo enmarcado: varias llamadas consecutivas a `dump()` no generan automáticamente un único documento válido. CSV requiere acordar dialecto y codificación; abre con `newline=""`, y los campos se leen como cadenas. XML es jerárquico; no confíes en entradas hostiles sin revisar seguridad y versión de Expat [37] [38] [39] [40].

```python
import json
perfil = {"nombre": "Ada", "activo": True}
texto = json.dumps(perfil, ensure_ascii=False, allow_nan=False)
recuperado = json.loads(texto)
print(recuperado["nombre"])
```

Salida esperada: `Ada`. No deserialices `pickle` de fuentes no confiables: un flujo malicioso puede ejecutar código [41].

## 10. Concurrencia y paralelismo

**Concurrencia** permite que tareas progresen en intervalos solapados; **paralelismo** implica ejecución simultánea. Selecciona el modelo según cuello de botella y API [42].

| Caso | Herramienta estándar | Consideración |
|---|---|---|
| I/O bloqueante | `threading`, `ThreadPoolExecutor` | Hilos comparten memoria; sincronizar estado. |
| CPU en CPython tradicional | `multiprocessing`, `ProcessPoolExecutor` | Procesos pueden usar varios núcleos; comunicación/serialización cuesta. |
| I/O asíncrona abundante | `asyncio` | Cooperativa; llamadas bloqueantes detienen el bucle. |
| Aislamiento de intérpretes | `InterpreterPoolExecutor` desde 3.14 | Datos no se comparten libremente; envío serializado. |

En CPython estándar, el GIL limita la ejecución simultánea de bytecode Python por hilos, aunque estos pueden solapar I/O y extensiones nativas que liberan el GIL pueden paralelizar. CPython ofrece builds free-threaded opcionales desde 3.13; no son predeterminadas y exigen comprobar extensiones, sincronización y rendimiento. No atribuyas el GIL a todo Python [43] [44].

```python
import asyncio

async def consultar(nombre):
    await asyncio.sleep(0.1)  # Simula espera asíncrona.
    return f"respuesta de {nombre}"

async def main():
    resultados = await asyncio.gather(consultar("A"), consultar("B"))
    print(resultados)

asyncio.run(main())
```

Salida esperada: `['respuesta de A', 'respuesta de B']`. `async def` crea una corutina; `await` cede el control. La función no se ejecuta en segundo plano solo por llamarla; debe esperarse o agendarse. Usa `TaskGroup` (3.11+) para vida estructurada. Un `Lock` protege invariantes compartidas; el GIL no reemplaza sincronización. Para procesos protege el punto de entrada con `if __name__ == "__main__":`; los métodos de inicio varían por plataforma y desde 3.14 `fork` ya no es predeterminado [45] [46] [47].

## 11. Errores, excepciones y depuración

Distingue error de sintaxis, excepción de ejecución y defecto lógico. Las excepciones derivan de `BaseException`; los fallos ordinarios derivan normalmente de `Exception`. `KeyboardInterrupt`, `SystemExit` y `GeneratorExit` están fuera de esa rama para no atraparlos con un `except Exception` ordinario [14] [48].

`try` delimita operaciones que pueden fallar; `except` captura tipos que se pueden manejar; `else` ocurre cuando no hubo excepción en `try`; `finally` sirve para limpieza. Captura lo específico y evita `except: pass`. No uses `return`, `break` o `continue` dentro de `finally` para alterar el flujo: pueden ocultar errores. Para recursos, prefiere `with` [14] [48].

```python
def convertir(texto):
    try:
        return int(texto)
    except ValueError as error:
        raise ValueError("se esperaba un entero") from error

try:
    convertir("doce")
except ValueError as error:
    print(error)
```

Salida esperada: `se esperaba un entero`. `raise ... from ...` conserva la causa. Las excepciones personalizadas deben heredar de `Exception` y representar condiciones que el llamador pueda tratar [49].

Un *traceback* muestra las llamadas hasta la excepción; empieza leyendo el tipo y mensaje al final, luego el marco más interno de tu código. `traceback` formatea trazas; `logging` registra eventos con niveles (`DEBUG`, `INFO`, `WARNING`, `ERROR`, `CRITICAL`). Usa `logging.getLogger(__name__)`; las bibliotecas no deberían imponer configuración global a la aplicación. `logger.exception()` dentro de `except` adjunta la traza [50] [51].

`pdb` es depurador estándar: `python -m pdb programa.py`; `breakpoint()` crea un punto de interrupción. Comandos usuales: `n` siguiente, `s` entrar, `c` continuar, `p expresión` imprimir, `where` mostrar pila, `q` salir [52]. `assert` expresa invariantes internas y puede desactivarse con `-O`; no lo uses para validar datos externos.

## 12. Seguridad

La seguridad depende del **contexto de destino**: validar una entrada, codificar HTML, parametrizar SQL y autorizar una acción son controles distintos. No existe una “sanitización” universal. Limita tamaño, tipo y rango de datos tan pronto crucen una frontera de confianza [53].

- **Procesos:** prefiere `subprocess.run([ejecutable, argumento], check=True, timeout=...)` con lista de argumentos. Evita `shell=True` con datos externos; fija ejecutable y valida también opciones interpretadas por el programa hijo. Particularidad: `.bat`/`.cmd` en Windows tiene matices de shell [54].
- **Serialización:** no uses `pickle` ni `shelve` con datos no confiables. JSON evita ejecución automática de código Python, pero sigue necesitando límites y validación de esquema [41].
- **SQL:** usa marcadores de parámetros del controlador (`?` en `sqlite3`); nunca f-strings ni concatenación para valores. Nombres de columnas/tablas no son valores parametrizables: selecciona desde una lista permitida. Parametrización no otorga autorización [55] [56].
- **Web:** HTML requiere codificación contextual. `html.escape()` ayuda para texto en HTML, pero no es codificador universal para JavaScript, CSS o URL. Preferir plantillas mantenidas con autoescape [57] [58].
- **Secretos:** `secrets` genera tokens criptográficamente fuertes; `random` es para simulación. No guardes claves en código, repositorios ni logs. Variables de entorno son mejores que literales, pero no una bóveda; en producción, considera un gestor de secretos y mínimo privilegio [59] [60].
- **Contraseñas:** no guardar texto claro ni hash rápido como `sha256(password)`. Usar una función de derivación lenta con sal única, parámetros medidos y formato versionado; OWASP recomienda Argon2id para nuevos sistemas y ofrece alternativas según requisitos [61]. Usa biblioteca especializada en producción.
- **Rutas:** resolver y comprobar contención reduce escapes sencillos, pero no elimina ataques de carrera ni enlaces simbólicos en directorios hostiles [35].
- **Dependencias:** instala en entornos aislados, evalúa procedencia/licencia/mantenimiento y audita vulnerabilidades conocidas. Una auditoría limpia no garantiza seguridad [62] [63].

La página oficial Security Considerations reúne advertencias sobre módulos como `pickle`, `subprocess`, `tempfile`, `ssl` y XML; consultarla junto a documentación del framework y avisos de dependencias es una práctica continua [53].

## 13. Herramientas, instalación y ciclo de desarrollo

### Instalación por sistema operativo

Comprueba primero la página oficial de descargas [1]. Los nombres de comandos no son universales; revisa la versión y ejecutable que usa el proyecto.

**Windows.** La vía actual recomendada por los borradores oficiales para CPython es Python install manager, desde python.org o Microsoft Store. En una terminal nueva:

```powershell
py install 3.15
py list
python --version
```

`py` selecciona y administra runtimes según la instalación. Los instaladores tradicionales `.exe` de versiones actuales conviven con instalaciones existentes, pero el instalador completo tradicional está obsoleto desde 3.14 según las fuentes consultadas; para una instalación nueva, prefiere el administrador [64].

**macOS.** Descarga el `.pkg` oficial compatible desde python.org, instala y completa `Install Certificates.command`. Puede haber también un Python de Apple en `/usr/bin/python3`; no lo elimines ni alteres. Comprueba cuál se invoca con `command -v python3` [65].

**Linux.** Usa preferentemente el gestor de paquetes de tu distribución, que puede ofrecer una versión distinta a la última de python.org. En Debian/Ubuntu:

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip
python3 --version
```

No reemplaces el Python del sistema. Si se necesita exactamente 3.15.2, compilar desde el código fuente requiere dependencias de compilación específicas de la distribución; `make altinstall` evita reemplazar el nombre genérico `python3`. La compilación no es el camino recomendado para todo principiante [66] [67].

### Primer programa y ejecución

Guarda como `hola.py`:

```python
print("¡Hola, Python!")
```

Ejecuta en la carpeta del archivo: Windows `python hola.py` (o `py hola.py`); macOS/Linux `python3 hola.py`. Salida esperada: `¡Hola, Python!`. La shell ejecuta el intérprete; el intérprete lee y ejecuta el archivo, compilando internamente bytecode cuando corresponde. No es necesario invocar un compilador por separado para este flujo [68].

Verifica versión, ruta y `pip` asociado:

```bash
python3 --version
python3 -c "import sys; print(sys.version); print(sys.executable)"
python3 -m pip --version
```

En Windows puedes emplear `python` según el administrador. La consola interactiva o REPL abre al ejecutar Python sin archivo; `>>>` acepta expresiones y `...` indica continuación. Para salir, `exit()` o EOF (`Ctrl+D` en Unix/macOS; `Ctrl+Z` y Enter en Windows) [68].

### Entorno virtual y dependencias

`venv` forma parte de la biblioteca estándar y separa paquetes de un proyecto; no instala por sí mismo otra versión de Python ni aísla el sistema operativo. Desde la raíz:

```bash
python3 -m venv .venv
source .venv/bin/activate  # macOS/Linux, Bash o Zsh
```

PowerShell:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

Windows `cmd.exe`: `.venv\Scripts\activate.bat`. Instala paquetes de terceros con `python -m pip install nombre-paquete` dentro del entorno; `python -m pip` evita mezclar pip de otro intérprete. Sal con `deactivate`. No subas `.venv` a Git; recréalo según dependencias declaradas [69] [70]. Si PowerShell impide activación, usa la ruta directa del intérprete del entorno en vez de cambiar una política global a ciegas.

### Editor, ciclo de trabajo y herramientas

IDLE suele acompañar CPython oficial; VS Code requiere instalar/seleccionar un intérprete y su extensión Python no instala Python por sí sola; PyCharm permite asociar un entorno [71] [72]. Un ciclo profesional típico: definir problema y versión objetivo → crear entorno → editar en módulos pequeños → ejecutar → probar casos normales/límite/error → depurar → revisar seguridad y calidad → documentar dependencias → construir y probar distribución.

`pyproject.toml` configura herramientas y empaquetado; no es ejecutable. `ruff`, `mypy`, `pytest`, `coverage.py` y `pip-audit` son herramientas de terceros; instálalas solo si el proyecto las adopta. `unittest`, `venv`, `argparse`, `logging`, `pdb`, `json`, `csv`, `pathlib` son parte de la biblioteca estándar [17] [28] [62] [73].

## 14. Pruebas de software

Las pruebas automatizadas verifican comportamiento seleccionado; no demuestran ausencia de defectos. Una prueba unitaria examina una unidad pequeña; integración prueba colaboración entre componentes; una prueba funcional valida un requisito observable, quizá atravesando varias capas. No son categorías que el ejecutor determine automáticamente [74].

`unittest` y `unittest.mock` son estándar. `pytest` y `coverage.py` son paquetes de terceros [75] [76] [77]. Ejemplo con `unittest`:

```python
# precios.py
def total_con_descuento(subtotal, porcentaje):
    if not 0 <= porcentaje <= 100:
        raise ValueError("porcentaje fuera de rango")
    return subtotal * (100 - porcentaje) // 100
```

```python
# test_precios.py
import unittest
from precios import total_con_descuento

class TestTotal(unittest.TestCase):
    def test_aplica_descuento(self):
        self.assertEqual(total_con_descuento(1000, 10), 900)

    def test_rechaza_porcentaje_invalido(self):
        with self.assertRaises(ValueError):
            total_con_descuento(1000, 120)
```

Ejecución: `python -m unittest -v`. Comprueba resultado y excepción, no detalles privados innecesarios. `pytest` permite funciones `test_`, `assert`, fixtures, parametrización y `tmp_path`; cobertura mide líneas/rutas ejecutadas, no calidad. Usa recursos temporales y limpieza; mocks prueban interacciones con sustitutos, no la integración real [75] [76] [77].

## 15. Ecosistema, biblioteca estándar y paquetes

### Diferencia esencial: estándar frente a terceros

La **biblioteca estándar** se distribuye con Python y sus módulos se importan sin instalarlos desde PyPI. Ejemplos: `pathlib`, `json`, `csv`, `datetime`, `re`, `collections`, `argparse`, `unittest`, `logging`, `sqlite3`, `asyncio`, `venv`. Algunos módulos dependen del sistema o de opciones de compilación [78].

Los **paquetes de terceros** no vienen incluidos, normalmente se instalan con pip desde PyPI u otro índice. Ejemplos: pytest, Django, Flask, FastAPI, NumPy, NetworkX, RxPY, Ruff. PyPI es un índice, no una certificación de calidad o seguridad. Revisa el proyecto correcto, licencia, soporte de Python/plataforma, mantenimiento, vulnerabilidades y dependencias transitivas [79] [80].

Un framework establece estructura y convenciones más amplias; una biblioteca suele ofrecer funciones que el programa llama. Django, Flask y FastAPI son ejemplos de frameworks web con filosofías distintas, no opciones intercambiables por simple popularidad [81] [82] [83]. Antes de instalar, comprueba si la estándar basta y declara las dependencias directas del proyecto.

### Dependencias, empaquetado y compatibilidad

`pyproject.toml` suele declarar `[build-system]` (backend), `[project]` (metadatos, `requires-python`, dependencias) y `[tool.*]` (ajustes de herramientas). Un backend genera distribuciones como wheel o sdist; pip las instala. `requirements.txt` puede servir al despliegue; `pip freeze` es una captura del entorno actual, no siempre una definición de proyecto completa. Para reproducibilidad más estricta se requieren versiones, hashes/procedencia y considerar plataforma/arquitectura [28] [30] [84].

Al corte consultado, las fuentes indicaban 3.15 y 3.14 en correcciones de errores; 3.13, 3.12 y 3.11 solo seguridad; 3.10 fin de vida el 1 de octubre de 2026. La política de cada dependencia es distinta: declara versiones probadas y ejecuta pruebas en las plataformas que prometes [2].

Para aprender APIs, parte de la documentación de la versión instalada: tutorial, referencia del lenguaje, biblioteca estándar, novedades y guías por plataforma. Para herramientas, consulta PyPA y documentación oficial de pip; para paquetes externos, su documentación y repositorio mantenido [78] [79] [85].

## 16. Buenas prácticas y calidad del código

Calidad significa que otras personas puedan entender, verificar y modificar código con riesgo razonable. PEP 8 recomienda `snake_case` para funciones/variables, `CapWords` para clases, constantes en mayúsculas, cuatro espacios y consistencia. PEP 257 orienta docstrings; son convenciones, no reglas que el intérprete imponga [11] [13].

Prefiere nombres que comuniquen propósito, funciones con responsabilidad clara, imports explícitos, `enumerate()` cuando se necesitan índice y elemento, `with` para recursos y comparaciones `is None`. El Zen de Python resume principios como legibilidad y explicitud; son heurísticas, no una prueba automática [86].

Docstrings aclaran propósito, parámetros, resultado, efectos y excepciones relevantes. Anotaciones aportan documentación y análisis estático, pero no validación dinámica. Refactorizar reorganiza sin cambiar comportamiento observable; cambia una cosa a la vez y apóyate en pruebas. DRY evita duplicar reglas que evolucionan juntas, no toda repetición textual; KISS favorece la solución simple que satisface requisitos [17] [87].

SOLID agrupa principios de diseño orientado a objetos (responsabilidad única, abierto/cerrado, sustitución de Liskov, segregación de interfaces, inversión de dependencias). Son heurísticas, no obligación de crear capas o jerarquías en scripts pequeños [88].

Herramientas externas como Ruff (lint/formato), mypy o Pyright (análisis estático) ayudan, pero no detectan toda lógica incorrecta ni reemplazan revisión. Acordar reglas, evitar herramientas redundantes y revisar cambios en contexto. Una revisión debe atender corrección, requisitos, seguridad, compatibilidad, claridad y pruebas; separar bloqueos de preferencias [89] [90].

## 17. Aplicabilidad entre lenguajes

Los fundamentos de descomposición, algoritmos, estructuras, pruebas y seguridad se transfieren; las reglas concretas cambian. No traslades mecánicamente supuestos sobre punteros, compilación, memoria, concurrencia o sistema de tipos [91].

| Área | Transferible | Específico que hay que reaprender |
|---|---|---|
| Algoritmos y Big O | Razonar sobre crecimiento, entrada y recursos. | Costes reales de contenedores e implementación. |
| Sintaxis y semántica | Distinguir forma válida y comportamiento. | Gramática, bloques por indentación y reglas Python. |
| Tipos | Validación, contratos y dominios. | Dinamismo, objetos, mutabilidad y alcance de anotaciones. |
| Estructuras | Elegir por operaciones. | `list`, `dict`, `set`, `deque`, hashabilidad y garantías. |
| Modularidad | Cohesión y dependencias explícitas. | Imports, paquetes, `__main__`, `venv`, `pyproject.toml`. |
| Memoria | Pensar en ciclo de vida y recursos. | Referencias y gestión del runtime; no hay ownership explícito general. |
| Concurrencia | Carrera, sincronización y límites. | GIL de CPython, asyncio, procesos y compatibilidad de APIs. |
| E/S y seguridad | Validación y separación de datos/código. | APIs estándar, codificaciones, parámetros, plantillas y modelos de permisos. |
| Pruebas/calidad | Casos, resultados, revisiones y documentación. | `unittest`, herramientas externas y convenciones del ecosistema. |

Al cambiar de lenguaje, conserva el razonamiento y estudia de nuevo el modelo de ejecución, tipos, errores, empaquetado y concurrencia antes de asumir equivalencias.

## 18. Cómo estudiar y utilizar esta guía

Ruta sugerida, de forma iterativa:

1. Instala Python, usa REPL y ejecuta `hola.py`; practica variables, tipos, expresiones y condicionales.
2. Resuelve problemas con bucles, funciones, listas/diccionarios y comprensión; explica entradas, salidas y casos límite.
3. Divide programas en módulos; usa `venv`, archivos, JSON/CSV y excepciones selectivas.
4. Añade pruebas automatizadas, depura con traceback o `pdb`, documenta y aplica estilo coherente.
5. Construye un paquete pequeño, administra dependencias y estudia seguridad y compatibilidad.
6. Aborda algoritmos, memoria, concurrencia y optimización cuando un proyecto lo requiera; perfila antes de optimizar.

No es necesario dominar los 16 apartados antes de programar. Estudia un concepto, implementa una solución sin copiar, prueba casos variados, depura fallos y vuelve a la guía cuando el proyecto presente una necesidad real. La meta es comprender y construir, no memorizar sintaxis.

## 19. Referencia rápida

| Necesidad | Forma habitual |
|---|---|
| Mostrar/leer | `print(valor)` / `texto = input("... ")` |
| Condición | `if condicion: ... elif ... else: ...` |
| Recorrer | `for elemento in iterable:`; índice y valor: `enumerate(iterable)` |
| Función | `def nombre(parametro) -> Tipo: ...` |
| Colecciones | `[]` lista; `()` tupla; `{clave: valor}` dict; `{elementos}` set no vacío |
| Comprensión | `[expresion for elemento in iterable if condicion]` |
| Excepción | `try: ... except TipoError: ... else: ... finally: ...` |
| Archivo | `with open(ruta, encoding="utf-8") as f:` |
| Módulo | `import modulo`; paquete: `python -m paquete.modulo` |
| Entorno | `python -m venv .venv`; instalar: `python -m pip install paquete` |
| Pruebas estándar | `python -m unittest` |
| Depuración | `python -m pdb programa.py` |

Operadores clave: aritmética `+ - * / // % **`; comparación `== != < <= > >=`; lógica `and or not`; pertenencia `in`; identidad `is None`. `=` asigna; `==` compara. En Windows el comando puede ser `python` o `py`; en macOS/Linux suele usarse `python3`.

## 20. Errores típicos de principiantes

1. **Olvidar `:` o sangría**: revisa cabeceras de bloques y usa cuatro espacios uniformes.
2. **Confundir `=` y `==`**: asigna con `=`, compara con `==`.
3. **Usar `is` para números/cadenas**: igualdad de valor con `==`; identidad `is None`.
4. **Esperar que `input()` devuelva número**: devuelve `str`; convierte y trata `ValueError`.
5. **Confundir alias con copia**: `b = a` comparte el objeto; copia explícitamente si el contrato lo requiere.
6. **Usar lista mutable como valor predeterminado**: crea la lista dentro de la función.
7. **Suponer que una anotación valida datos**: valida entradas externas explícitamente.
8. **Capturar toda excepción o ignorarla**: captura el error específico solo si puedes recuperarte.
9. **Modificar colección mientras se itera**: filtra a una colección nueva o itera sobre copia apropiada.
10. **Instalar con un `pip` distinto**: ejecuta `python -m pip` con el intérprete del proyecto.
11. **Usar `list.pop(0)` como cola**: usa `collections.deque.popleft()`.
12. **Abrir archivos sin `with` o sin codificación**: administra el recurso y declara formato/codificación.
13. **Nombrar un archivo `json.py`, `typing.py` o `random.py`**: puede ocultar módulos estándar.
14. **Creer que ejecutar `async def` la agenda automáticamente**: espera o crea una tarea y recoge errores.
15. **Suponer que concurrencia es paralelismo** o que el GIL corrige carreras: identifica el modelo y sincroniza invariantes.

## 21. Ejercicios progresivos

Intenta resolverlos antes de consultar las soluciones. Usa solo biblioteca estándar salvo indicación.

1. **Saludo personalizado.** Lee un nombre y muestra `Hola, NOMBRE`. Define el comportamiento ante una línea vacía.
2. **Conversor de temperatura.** Implementa Celsius a Fahrenheit; prueba 0 °C y un valor negativo.
3. **Contador de palabras.** Dada una frase, cuenta palabras ignorando espacios repetidos y muestra la más frecuente.
4. **Validador de rango.** Escribe una función que acepte un entero de 1 a 100 y rechace entradas no numéricas o fuera del rango con un mensaje claro.
5. **Inventario.** Usa un `dict` para aplicar operaciones de suma y consulta, y maneja artículos inexistentes.
6. **Cola FIFO.** Implementa una cola de tareas con `collections.deque` y procesa hasta vaciarla.
7. **Archivo JSON.** Guarda un diccionario en UTF-8 y vuelve a cargarlo; valida la presencia y tipo de un campo.
8. **Prueba automatizada.** Escribe dos pruebas `unittest` para una función de descuento: caso normal y porcentaje inválido.
9. **Frecuencia eficiente.** Cuenta elementos repetidos en una lista; explica coste temporal y espacio de tu método.
10. **Concurrencia.** Convierte dos operaciones asíncronas simuladas con `asyncio.sleep` y compara espera secuencial con `gather`; explica por qué no prueba paralelismo CPU.

## 22. Soluciones de los ejercicios

Las soluciones son ejemplos posibles, no las únicas respuestas correctas.

### Ejercicio 1

```python
nombre = input("Nombre: ").strip()
if not nombre:
    nombre = "invitada"
print(f"Hola, {nombre}")
```

### Ejercicio 2

```python
def celsius_a_fahrenheit(celsius: float) -> float:
    return celsius * 9 / 5 + 32

print(celsius_a_fahrenheit(0))
print(celsius_a_fahrenheit(-10))
```

Salida esperada: `32.0` y `14.0`.

### Ejercicio 3

```python
from collections import Counter

frase = "Python es claro y Python es práctico"
palabras = frase.casefold().split()
frecuencias = Counter(palabras)
print(len(palabras), frecuencias.most_common(1))
```

Salida esperada: `7 [('python', 2)]`.

### Ejercicio 4

```python
def validar_rango(texto: str) -> int:
    try:
        numero = int(texto)
    except ValueError as error:
        raise ValueError("escribe un entero") from error
    if not 1 <= numero <= 100:
        raise ValueError("el valor debe estar entre 1 y 100")
    return numero
```

### Ejercicio 5

```python
inventario = {"cuaderno": 4, "lápiz": 10}

def sumar_articulo(nombre: str, cantidad: int) -> None:
    if cantidad < 0:
        raise ValueError("cantidad negativa")
    inventario[nombre] = inventario.get(nombre, 0) + cantidad

sumar_articulo("cuaderno", 2)
print(inventario["cuaderno"])
print(inventario.get("regla", 0))
```

Salida esperada: `6` y `0`.

### Ejercicio 6

```python
from collections import deque

cola = deque(["tarea-1", "tarea-2", "tarea-3"])
while cola:
    tarea = cola.popleft()
    print("Procesando", tarea)
```

### Ejercicio 7

```python
import json
from pathlib import Path

ruta = Path("datos.json")
ruta.write_text(json.dumps({"nombre": "Ada", "activo": True}), encoding="utf-8")
datos = json.loads(ruta.read_text(encoding="utf-8"))
if not isinstance(datos, dict) or not isinstance(datos.get("activo"), bool):
    raise ValueError("esquema inválido")
print(datos["nombre"], datos["activo"])
```

Salida esperada: `Ada True`. En un proyecto real, el archivo creado debe tener una ubicación y ciclo de vida definidos.

### Ejercicio 8

```python
import unittest

def descuento(centimos: int, porcentaje: int) -> int:
    if centimos < 0 or not 0 <= porcentaje <= 100:
        raise ValueError("argumentos fuera de rango")
    return centimos * (100 - porcentaje) // 100

class TestDescuento(unittest.TestCase):
    def test_normal(self):
        self.assertEqual(descuento(1000, 10), 900)

    def test_porcentaje_invalido(self):
        with self.assertRaises(ValueError):
            descuento(1000, 101)
```

Guarda el archivo y ejecuta `python -m unittest -v`.

### Ejercicio 9

```python
from collections import Counter

valores = ["a", "b", "a", "c", "b", "a"]
frecuencias = Counter(valores)
print(frecuencias)
```

Para elementos hashables, el patrón suele ser O(n) tiempo promedio y O(k) espacio, con `k` valores distintos. El coste concreto depende de hashing e implementación.

### Ejercicio 10

```python
import asyncio

async def tarea(nombre):
    await asyncio.sleep(0.1)
    return nombre

async def main():
    resultados = await asyncio.gather(tarea("A"), tarea("B"))
    print(resultados)

asyncio.run(main())
```

Salida esperada: `['A', 'B']`. Las esperas se solapan cooperativamente; el ejemplo no ejecuta cálculo Python en dos núcleos.

## 23. Mini proyectos

### 1. Gestor de tareas de consola — principiante

Crea, lista, completa y elimina tareas. Usa listas o diccionarios, funciones, `input()`, bucles y validación. Extensión: guardar/cargar JSON. Criterios: no perder datos ante entrada inválida; separar lógica de interacción; probar operaciones de agregar y completar.

### 2. Analizador de archivos CSV — intermedio

Lee ventas desde CSV con `csv.DictReader`, convierte cantidades de forma explícita, calcula totales y genera un resumen JSON o CSV. Usa `pathlib`, codificación UTF-8, `Decimal` si hay requisitos monetarios decimales, manejo de excepciones y pruebas con archivos temporales. Criterios: reportar fila inválida, no cargar archivos sin límite si el volumen es grande y documentar el dialecto.

### 3. API de catálogo o servicio web — intermedio/avanzado

Construye una API pequeña con FastAPI o Flask (terceros; deben instalarse y fijarse en el proyecto). Organiza lógica en paquete, valida solicitudes, usa base de datos con consultas parametrizadas, escribe pruebas unitarias e integración y mantiene secretos fuera del código. Criterios: autorización diferenciada de validación, dependencias declaradas, logs sin credenciales y pruebas reproducibles.

### 4. Procesador concurrente de trabajos — avanzado

Toma un conjunto de tareas de I/O, implementa versión secuencial y versión `asyncio` o `ThreadPoolExecutor`, limita concurrencia y define timeout/cancelación. Mide con cargas representativas y compara resultados. Criterios: errores propagados, cierre ordenado, ausencia de estado compartido innecesario y explicación de por qué la solución elegida responde al cuello de botella.

## 24. Glosario

- **Alias:** nombre o contenedor adicional que referencia el mismo objeto.
- **Anotación de tipo:** metadato de tipos para documentación y herramientas; no validación automática general.
- **Bytecode:** representación intermedia que ejecuta la máquina virtual de CPython.
- **Cierre (closure):** función que conserva acceso a nombres de ámbitos envolventes.
- **Concurrencia:** progreso solapado de tareas; no implica ejecución simultánea.
- **Entorno virtual (`venv`):** entorno Python aislado por proyecto para paquetes.
- **Excepción:** objeto que señala una condición de error o control durante ejecución.
- **Framework:** conjunto de estructura y convenciones que organiza una aplicación.
- **Hashable:** objeto con hash estable y compatible con igualdad, utilizable en `dict`/`set`.
- **Iterable:** objeto cuyos elementos pueden recorrerse.
- **Mutabilidad:** capacidad de cambiar el valor de un objeto conservando su identidad.
- **Paquete:** módulo con espacio de nombres jerárquico, normalmente directorio importable.
- **PyPI:** índice público de distribuciones Python, no certificación de calidad.
- **REPL:** consola que lee, evalúa y muestra resultados interactivamente.
- **Serialización:** conversión de datos a una representación para almacenar o transmitir.
- **Tipado dinámico:** tipos asociados a objetos en ejecución, sin declaración estática obligatoria por nombre.
- **Wheel:** formato de distribución construida instalable de paquetes Python.

## 25. Documentación y fuentes oficiales

Para ampliar con fuentes primarias, empieza por la [documentación oficial de Python](https://docs.python.org/3/), su [tutorial](https://docs.python.org/3/tutorial/) y la [referencia del lenguaje](https://docs.python.org/3/reference/). Para instalación consulta las páginas oficiales de [Windows](https://docs.python.org/3/using/windows.html), [macOS](https://docs.python.org/3/using/mac.html) y [Unix/Linux](https://docs.python.org/3/using/unix.html). Para empaquetado y publicación, consulta la [Python Packaging User Guide de PyPA](https://packaging.python.org/en/latest/); para índices de paquetes, [PyPI](https://pypi.org/). PEP 8, PEP 257 y los PEP de tipado describen convenciones y propuestas aceptadas, con alcance indicado en cada documento. Las páginas de proyectos externos no reemplazan revisar versión, licencia y soporte.

# Referencias bibliográficas

Fuentes oficiales y documentación técnica utilizadas para elaborar esta guía. Se priorizan la documentación oficial de Python, las PEP, PyPA y herramientas reconocidas del ecosistema.

## 1. Python: fundamentos y documentación general

- [1. Python 3.15.2](https://www.python.org/downloads/release/python-3152/)
- [2. Estado de las versiones de Python](https://devguide.python.org/versions/)
- [3. FAQ general de Python](https://docs.python.org/3/faq/general.html)
- [4. El tutorial oficial de Python](https://docs.python.org/3/tutorial/index.html)
- [5. Acerca de Python](https://www.python.org/about/)
- [6. Fin del soporte de Python 2](https://www.python.org/doc/sunset-python-2/)
- [7. PEP 602: ciclo anual de versiones de Python](https://peps.python.org/pep-0602/)
- [8. Aplicaciones de Python](https://www.python.org/about/apps/)
- [85. Documentación de Python](https://www.python.org/doc/)
- [86. PEP 20: el Zen de Python](https://peps.python.org/pep-0020/)

## 2. Sintaxis, estructura y estilo del lenguaje

- [9. Referencia del lenguaje: análisis léxico](https://docs.python.org/3.15/reference/lexical_analysis.html)
- [10. Referencia del lenguaje: expresiones](https://docs.python.org/3.15/reference/expressions.html)
- [11. PEP 8: guía de estilo para código Python](https://peps.python.org/pep-0008/)
- [12. Referencia del lenguaje: sentencias compuestas](https://docs.python.org/3.15/reference/compound_stmts.html)
- [13. PEP 257: convenciones de docstrings](https://peps.python.org/pep-0257/)
- [14. Excepciones incorporadas](https://docs.python.org/3.15/library/exceptions.html)
- [15. Modelo de datos de Python](https://docs.python.org/3.15/reference/datamodel.html)
- [16. Tipos incorporados](https://docs.python.org/3.15/library/stdtypes.html)
- [17. typing: soporte para sugerencias de tipos](https://docs.python.org/3.15/library/typing.html)
- [18. Especificación del sistema de tipos](https://typing.python.org/en/latest/spec/concepts.html)
- [19. Tutorial: herramientas de control de flujo](https://docs.python.org/3.15/tutorial/controlflow.html)
- [20. Modelo de ejecución de Python](https://docs.python.org/3.15/reference/executionmodel.html)
- [34. Funciones incorporadas](https://docs.python.org/3.15/library/functions.html)
- [42. Glosario: concurrencia, paralelismo y GIL](https://docs.python.org/3.15/glossary.html)

## 3. Estructuras de datos y programación orientada a objetos

- [21. Tutorial: estructuras de datos](https://docs.python.org/3.15/tutorial/datastructures.html)
- [22. Complejidad temporal de operaciones en tipos integrados de CPython](https://docs.python.org/3.15/builtins/time-complexity.html)
- [23. Tutorial de NetworkX](https://networkx.org/documentation/stable/tutorial.html)
- [24. collections: tipos de datos contenedores](https://docs.python.org/3.15/library/collections.html)
- [25. Tutorial: clases](https://docs.python.org/3.15/tutorial/classes.html)
- [26. RxPY: primeros pasos](https://rxpy.readthedocs.io/en/latest/get_started.html)

## 4. Módulos, paquetes y gestión de memoria

- [27. Sistema de importación](https://docs.python.org/3.15/reference/import.html)
- [28. Empaquetar proyectos Python](https://packaging.python.org/en/latest/tutorials/packaging-projects/)
- [29. Empaquetado de paquetes de espacio de nombres](https://packaging.python.org/en/latest/guides/packaging-namespace-packages/)
- [30. Escribir pyproject.toml](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/)
- [31. gc: interfaz del recolector de basura](https://docs.python.org/3.15/library/gc.html)
- [33. Conteo de referencias en la C API](https://docs.python.org/3.15/c-api/refcounting.html)

## 5. Archivos, entrada/salida y formatos de datos

- [35. pathlib: rutas del sistema de archivos](https://docs.python.org/3.15/library/pathlib.html)
- [36. io: herramientas para flujos](https://docs.python.org/3.15/library/io.html)
- [37. json: codificador y decodificador](https://docs.python.org/3.15/library/json.html)
- [38. csv: lectura y escritura](https://docs.python.org/3.15/library/csv.html)
- [39. xml.etree.ElementTree: API XML](https://docs.python.org/3.15/library/xml.etree.elementtree.html)
- [40. Procesamiento XML y seguridad](https://docs.python.org/3.15/library/xml.html)
- [41. pickle: serialización de objetos Python](https://docs.python.org/3.15/library/pickle.html)

## 6. Concurrencia, paralelismo y programación asíncrona

- [43. threading: paralelismo basado en hilos](https://docs.python.org/3.15/library/threading.html)
- [44. Compatibilidad de Python con free threading](https://docs.python.org/3.15/howto/free-threading-python.html)
- [45. asyncio: corutinas y tareas](https://docs.python.org/3.15/library/asyncio-task.html)
- [46. multiprocessing: paralelismo basado en procesos](https://docs.python.org/3.15/library/multiprocessing.html)
- [47. concurrent.futures: ejecución concurrente de funciones](https://docs.python.org/3.15/library/concurrent.futures.html)

## 7. Manejo de errores, depuración y registros

- [48. Tutorial: errores y excepciones](https://docs.python.org/3.15/tutorial/errors.html)
- [49. PEP 3134: encadenamiento de excepciones](https://peps.python.org/pep-3134/)
- [50. traceback: imprimir o recuperar una traza](https://docs.python.org/3.15/library/traceback.html)
- [51. logging: sistema de registro de eventos](https://docs.python.org/3.15/library/logging.html)
- [52. pdb: depurador de Python](https://docs.python.org/3.15/library/pdb.html)

## 8. Seguridad y buenas prácticas

- [53. Consideraciones de seguridad](https://docs.python.org/3.15/library/security_warnings.html)
- [54. subprocess: gestión de subprocesos](https://docs.python.org/3.15/library/subprocess.html)
- [55. sqlite3: interfaz de bases de datos SQLite](https://docs.python.org/3.15/library/sqlite3.html)
- [56. OWASP: prevención de inyección SQL](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
- [57. html: utilidades HTML](https://docs.python.org/3.15/library/html.html)
- [58. OWASP: prevención de XSS](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
- [59. secrets: generación de valores secretos](https://docs.python.org/3.15/library/secrets.html)
- [60. OWASP: gestión de secretos](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html)
- [61. OWASP: almacenamiento de contraseñas](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)
- [62. pip-audit: auditoría de vulnerabilidades de paquetes](https://github.com/pypa/pip-audit)
- [63. pip: instalaciones seguras](https://pip.pypa.io/en/stable/topics/secure-installs/)

## 9. Instalación, configuración y entornos de desarrollo

- [64. Uso de Python en Windows](https://docs.python.org/3.15/using/windows.html)
- [65. Uso de Python en macOS](https://docs.python.org/3.15/using/mac.html)
- [66. Uso de Python en plataformas Unix](https://docs.python.org/3.15/using/unix.html)
- [67. Configuración y construcción de Python](https://docs.python.org/3.15/using/configure.html)
- [68. Tutorial: uso del intérprete de Python](https://docs.python.org/3.15/tutorial/interpreter.html)
- [69. venv: creación de entornos virtuales](https://docs.python.org/3.15/library/venv.html)
- [70. Instalar paquetes en un entorno virtual](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/)
- [71. Editores e IDE](https://docs.python.org/3.15/using/editors.html)
- [72. Introducción a Python en Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial)
- [73. Tutorial de Ruff](https://docs.astral.sh/ruff/tutorial/)
- [84. pip: instalaciones repetibles](https://pip.pypa.io/en/stable/topics/repeatable-installs/)

## 10. Pruebas y calidad del software

- [74. unittest: marco de pruebas unitarias](https://docs.python.org/3.15/library/unittest.html)
- [75. unittest.mock: biblioteca de objetos simulados](https://docs.python.org/3.15/library/unittest.mock.html)
- [76. pytest: primeros pasos](https://docs.pytest.org/en/stable/getting-started.html)
- [77. coverage.py: medir ejecución](https://coverage.readthedocs.io/en/latest/commands/cmd_run.html)

## 11. Biblioteca estándar, paquetes y frameworks

- [78. Biblioteca estándar de Python](https://docs.python.org/3.15/library/index.html)
- [79. Ayuda de PyPI](https://pypi.org/help/)
- [80. PyPA: recomendaciones de herramientas](https://packaging.python.org/en/latest/guides/tool-recommendations/)
- [81. Django: visión general](https://docs.djangoproject.com/en/6.1/intro/overview/)
- [82. Documentación de Flask](https://flask.palletsprojects.com/en/stable/)
- [83. Documentación de FastAPI](https://fastapi.tiangolo.com/)

## 12. Lecturas complementarias

- [87. Refactoring: Martin Fowler](https://refactoring.com/)
