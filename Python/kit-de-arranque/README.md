# Kit de Arranque

La idea detrás de este Kit es que si ya eres programador puedas comenzar a 
programar en Python en tiempo record. Obviamente no se describirá el lenguaje en
toda su extensión pero si podrá hacer uso de lo aprendido para iniciar su 
programa o proyecto. Python cuenta con una gran cantidad de librerías y 
componentes, por lo que con lo aprendido acá y haciendo uso de la documentación
adecuada podrá avanzar en el desarrollo de interfaces gráficas, servicios web u
otras aplicaciones.

## Consideraciones Iniciales

Este kit se ha escrito utilizando GNU/Linux, si usted es usuario de MS Windows
deberá hacer los ajustes en cuanto al uso de la línea de comandos y algunas
configuraciones. No recomendamos el uso de UN editor de texto en particular pero
será necesario que usted maneje bien el que vaya a utilizar pues será su 
herramienta de trabajo. Así mismo debe tener la habilidad suficiente en el uso
del terminal para que pueda escribir los comandos que se indiquen. 

Adicionalmente este tutorial trata la versión 2.6 de Python, que es la difundida
con la versión estable de Debian. En general los conceptos son los igualmente
válidos para la versión 2.7, sin embargo si usted va a utilizar la versión 3.x
del lenguaje deberá observar las diferencias.

## Lo Básico explicado en 15 Minutos

Bueno, realmente no le tomará 15 minutos aprender todo lo que se nombra acá, 
sin embargo si será el tiempo aproximado para leer todo el contenido por 
primera vez. Ahora sin más, comencemos:

### Uso

Python es un [lenguaje de programación interpretado][lenguaje-interpretado] lo
que significa que una vez escrito un programa podrá hacer ejecutarlos 
directamente. Así mismo esta característica permite que pueda interactuar con
el lenguaje mediante un modo interactivo del intérprete.

Para iniciar una conversación con Python simplemente escriba en su terminal:

    $ python
    Python 2.6.6 (r266:84292, Dec 27 2010, 00:02:40) 
    [GCC 4.4.5] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> 

y obtendrá un prompt con el símbolo `>>>` que le indica que de allí en 
adelante usted debe ejecutar instrucciones Python.

Por otro lado, los programas escritos con este lenguaje se nombran con la
extensión *.py*. Si usted desea ejecutar su programa *hola_mundo.py* usted 
deberá escribir la instrucción:

    $ python hola_mundo.py
    Hola Mundo!
    $


### Estructura de un Programa

Mucho del trabajo que se realiza con Python se hace desde el intérprete 
interactivo. Es por ello que para escribir un programa en Python simplemente
copie sus instrucciones en un archivo con extensión *.py* y ejecútelo.

Sin embargo si quiere escribir un programa largo o complejo es recomendable
que tome en cuenta el siguiente esquema

    #/usr/bin/env python
    # -*- coding: utf-8 -*-
    
    from ... import ...

    ["sus", "clases", "funciones", "etc."]
    
    if __name__ == "__main__":
        ["inicio de ejecución"]

Ahora bien, ¿qué significa cada linea?

* `#/usr/bin/env python` le dice la línea de comandos de \*NIX el intérprete
que usará para el programa es Python
* `# -*- coding: utf-8 -*-` indica a python que la codificación del archivo
es UTF-8 (importante para nuestro idioma).
* `import ...` o `from ... import ...` es la sección donde cargamos los módulos
que utilizamos junto con sus espacios de nombres (esto se verá con detalle en
el apartado dedicado a trabajar con módulos).
* En la siguiente sección siéntase libre de escribir sus variables, funciones,
clases, etc. que considere necesarios para su programa.
* `if __name__ == "__main__":` es la condición que dice indica al intérprete
el inicio de la ejecución propiamente dicha. Es el equivalente a la 
declaración de la función `main` en otros lenguajes.
* Lo que sigue a la condición anterior es lo que ejecuta el programa como
rutinas al inicio.

La filosofía de Python podemos verla mediante el comando `$ python -c "import 
this"`:

    The Zen of Python, by Tim Peters

    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!

Uno de los efectos prácticos es que normalmente Python convierte en ley lo que
se entiende como buenas prácticas, un ejemplo de ello es que los bloques de 
código se declaran mediante indentación. Así mismo, el final de cada línea 
ya tiene los caracteres especiales que la define, tomando en cuenta este hecho
Python toma en cuenta estos caracteres evitando la necesidad del `;`. Otras 
reglas de estilo y de uso se verán en los distintos ejemplos de la guía.

### Variables

¿Qué diría que tiene en frente si tiene pico plano, plumas impermeables, patas
palmípedas y hace _cuack_? Un pato, ¿cierto? para Python la declaración de
variables es de este modo. Si un dato que va a almacenar se comporta como un 
entero el lenguaje dice "Hey! es un número entero!". Es así como para declarar
una variable solo debes decir a Python que a vas guardar un valor con un
nombre. Veamos un ejemplo, abra un terminal y escriba:

    $ python
    Python 2.6.6 (r266:84292, Dec 27 2010, 00:02:40) 
    [GCC 4.4.5] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> a = 5
    >>> type(a)
    <type 'int'>
    >>> b = 12.0
    >>> type(b)
    <type 'float'>
    >>> c = 4 -5j
    >>> type(c)
    <type 'complex'>
    >>> d = True
    >>> type(d)
    <type 'bool'>
    >>> e = "Hola Mundo!"
    >>> type(e)
    <type 'str'>
    >>>

__Ejercicio__: dentro del mismo terminal, igual que se hizo con la función
`type()` aplique la función `dir()`. La lista que recibirá son la serie de
funciones y atributos de cada variable.

¿Sorprendido? esto es lo que se conoce como __introspección__ y es posible
debido a que Python es orientado a objetos, por ende una variable es un
objeto y tiene sus estructuras. Los elementos llamados \_\_algo\_\_ son los
llamados métodos especiales. Ya veremos cómo se come eso en el apartado de
__Clases y Objetos__.

### Funciones

Para los programadores que provienen de lenguajes donde se diferencian los 
procedimientos de las funciones, aquí la primera noticia: En Python todas son
funciones. 


### Control de Flujo de Programa

#### Alternativas Lógicas

#### Bucles

### Clases y Objetos

## Lo demás explicado en otros 15 minutos

### Módulos

### Expresiones Regulares 

### Un Poquito de Bases de Datos

### Uso de Entornos Virtuales


## Colaboradores

* [Carlos G. Ruiz](http://atmantree.com)


[lenguaje-interpretado]: http://es.wikipedia.org/wiki/Lenguaje_de_programaci%C3%B3n_interpretado 


