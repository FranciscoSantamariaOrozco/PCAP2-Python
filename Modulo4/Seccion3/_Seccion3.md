#  
[Ejercicios](/Modulo4/Seccion3/Sec3-ej.md)
<br></br>

[Soluciones](/Modulo4/Seccion3/Sec3-ejsol.md)  

#

[Volver a: Módulo 4 - Miscelaneo](../README.md)

# **Trabajando con archivos reales**  

<br></br>  


En esta lección vamos a preparar un archivo de texto simple con contenido breve y simple.  
```python
# Se abre el archivo tzop.txt en modo lectura, devolviéndolo como un objeto del tipo archivo:
stream = open("tzop.txt", "rt", encoding = "utf-8")

# Se imprime el contenido del archivo:
print(stream.read()) 
```

Te mostraremos algunas técnicas básicas que puedes utilizar para leer el **contenido del archivo** y poder  
procesarlo.  

El procesamiento será muy simple: vas a copiar el contenido del archivo a la consola y contarás todos los  
caracteres que el programa ha leído. 

Pero recuerda: nuestra compresión de un archivo de texto es muy estricta. Es un archivo de texto sin formato:  
puede contener solo texto, sin decoraciones adicionales (formato, diferentes fuentes, etc...).  

Es por eso que debes evitar crear el archivo utilizando un procesador de texto avanzado como MS Word, LibreOffice Writer o algo así. Utiliza los conceptos básicos que ofrece tu sistema operativo: Block de notas, vim, gedit, etc.

Si tus archivos de texto contienen algunos caracteres nacionales no cubiertos por el juego de caracteres ASCII  
estándar, es posible que necesites un paso adicional. La invocación de tu función ```open()``` puede requerir un  
argumento que denote una codificación específica del texto.  

Por ejemplo, si estás utilizando un sistema operativo Unix/Linux configurado para usar UTF-8 como una  
configuración de todo el sistema, la función ```open()``` puede verse de la siguiente manera:  
```
stream = open('file.txt', 'rt', encoding='utf-8')
```  

Donde el argumento de codificación debe establecerse en un valor dentro de una cadena que representa la  
codificación de texto adecuada (UTF-8, en este caso).  

Consulta la documentación de tu sistema operativo para encontrar el nombre de codificación adecuado para tu  
entorno.  

```Nota```  
A los fines de nuestros experimentos con el procesamiento de archivos que se llevan a cabo en esta sección,  
vamos a utilizar un conjunto de archivos precargados (p. Ej., los archivos *tzop.txt*, o *text.txt*) con los cuales  
podrás trabajar. Si deseas trabajar con tus propios archivos localmente en tu máquina, te recomendamos que lo hagas y que utilices IDLE o cualquier otro Entorno de Desarollo para llevar a cabo tus propias pruebas.  

<br></br>  


## **Procesamiento de archivos de texto: continuación**  
La lectura del contenido de un archivo de texto se puede realizar utilizando diferentes métodos; ninguno de  
ellos es mejor o peor que otro. Depende de ti cual de ellos prefieres y te gusta.  

Algunos de ellos serán a veces más prácticos y otros más problemáticos. Se flexible. No tengas miedo de  
cambiar tus preferencias.  

El más básico de estos métodos es el que ofrece la función ```read()```, la cual pudiste ver en acción en la lección anterior.  

Si se aplica a un archivo de texto, la función es capaz de:  
- Leer un número determinado de caracteres (incluso solo uno) del archivo y devolverlos como una cadena.  
- Leer todo el contenido del archivo y devolverlo como una cadena.  
- Si no hay nada más que leer (el cabezal de lectura virtual llega al final del archivo), la función devuelve una cadena vacía.  

Comenzaremos con la variante más simple y usaremos un archivo llamado ```text.txt```. El archivo contiene lo siguiente:
```
Lo hermoso es mejor que lo feo.
Explícito es mejor que implícito.
Simple es mejor que complejo.
Complejo es mejor que complicado.
```  
<br></br>

Ahora observa el código en el editor y analicémoslo.  
```python
from os import strerror

try:
    counter = 0
    stream = open('text.txt', "rt")
    char = stream.read(1)
    while char != '':
        print(char, end='')
        counter += 1
        char = stream.read(1)
    stream.close()
    print("\n\nCaracteres en el archivo:", counter)
except IOError as e:
    print("Se produjo un error de E/S:", strerror(e.errno))
```  

La rutina es bastante simple:  

- Se usa el mecanismo try-except y se abre el archivo con el nombre (text.txt en este caso).
- Intenta leer el primer carácter del archivo (```char = stream.read(1)```).  
- Si tienes éxito (esto se demuestra por el resultado positivo de la condición ```while```), se muestra el carácter  
(nota el argumento ```end=```, es importante! No querrás saltar a una nueva línea después de cada  
carácter!).  
- También, se actualiza el contador (counter)  .
- Intenta leer el siguiente carácter y el proceso se repite.  

<br></br>  


## **Procesamiento de archivos de texto: continuación**  
Si estás absolutamente seguro de que la longitud del archivo es segura y puedes leer todo el archivo en la  
memoria de una vez, puedes hacerlo: la función ```read()```, invocada sin ningún argumento o con un argumento  
que se evalúa a ```None```, hará el trabajo por ti.  

Recuerda: **el leer un archivo muy grande (en terabytes) usando este método puede dañar tu sistema**  
**operativo**.  

No esperes milagros: la memoria de la computadora no se puede extender.  

Observa el código en el editor. Qué piensas de el?  
```python
from os import strerror

try:
    counter = 0
    stream = open('text.txt', "rt")
    content = stream.read()
    for char in content:
        print(char, end='')
        counter += 1
    stream.close()
    print("\n\nCaracteres en el archivo:", counter)
except IOError as e:
    print("Se produjo un error de E/S:", strerr(e.errno))
```  

Vamos a analizarlo:  
- Abre el archivo, como anteriormente se hizo.  
- Lee el contenido mediante una invocación de la función ```read()```.  
- Después, se procesa el texto, iterando con un bucle ```for``` su contenido, y se actualiza el valor del contador  
en cada vuelta del bucle.  

El resultado será exactamente el mismo que en el ejemplo anterior.  

<br></br>  


## **Procesando archivos de texto: *readline()***  
Si deseas manejar el contenido del archivo **como un conjunto de líneas**, no como un montón de caracteres, el  
método ```readline()``` te ayudará con eso.  

El método intenta **leer una línea completa de texto del archivo**, y la devuelve como una cadena en caso de  
éxito. De lo contrario, devuelve una cadena vacía.  

Esto abre nuevas oportunidades: ahora también puedes contar líneas fácilmente, no solo caracteres.  

Hagamos uso de ello. Observa el código en el editor.  
```python
from os import strerror

try:
    character_counter = line_counter = 0
    stream = open('text.txt', 'rt')
    line = stream.readline()
    while line != '':
        line_counter += 1
        for char in line:
            print(char, end='')
            character_counter += 1
        line = stream.readline()
    stream.close()
    print("\n\nCaracteres en el archivo:", character_counter)
    print("Líneas en el archivo:     ", line_counter)
except IOError as e:
    print("Se produjo un error de E/S:", strerror(e.errno))
```  

Como puedes ver, la idea general es exactamente la misma que en los dos ejemplos anteriores.  

<br></br>  


## **Procesando archivos de texto: *readlines()***  
Otro método 