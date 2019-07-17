# Para trabajar en Markdown
pandoc -f markdown -t html respuestas.md > respuestas.html
firefox respuestas.html

1. Escriban qué esperan de cada uno de los pasos

    1. Pre-procesador: `make preprocessing`
    gcc -E calculator.c -o calculator.pp.c

    Espero un archivo escrito en lenguaje c generado por el pre-compilador, así evito tener que
    definir funciones y macros usuales.

    2. Compilacion I: `make assembler`
    gcc -S calculator.c -o calculator.asm

    Espero un archivo escrito en lenguaje Assembler.
    Esta etapa esta separda en 3 subsecciones:
        a.`El front end`: Análisis sintáctico, semántico y léxico.
        Genera una intermediate representation (IR)
        b. `El middle end`: Toma la IR del front end y la
        optimiza -vamos a ver en otras clases cómo-.
        c. `El back end`: Genera el código de assembler y
        realiza optimizaciones de hardware (por ejemplo,
        elige qué registros se utilizan para las variables)

    3. Compilacion II: `make object`
    gcc -c calculator.c -o calculator.o

    Espero un archivo objeto escrito en binario. En esta etapa el objeto no es ejecutable

    4. Linkeo: `make executable`
    gcc calculator.o -o calculator.e

    Hago ejecutable al objeto, linkeando a las librerias que este necesita para poder ejecutarse. 


# gcc --help
-E            Preprocess only; do not compile, assemble or link
-S            Compile only; do not assemble or link
-c            Compile and assemble, but do not link
-o <file>     Place the output into <file>

2. ¿Qué agregó el preprocesador?
    Agregó funciones y macros, evitando que los haya tenido que agregar en la etapa de desarrollo. 


3. Identificar en la rutina de assembler las funciones

4. Explicar qué quieren decir los símbolos que se crean en el objeto

5. ¿En qué se diferencian los símbolos del objeto y del ejecutable?

    a. nm calculator.o

        1. 000000000000003c T add_numbers
        2. 0000000000000000 T main
        3.         U printf


