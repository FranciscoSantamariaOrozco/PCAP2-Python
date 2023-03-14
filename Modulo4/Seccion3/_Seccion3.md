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
Otro método, que maneja el archivo de texto como un conjunto de líneas, no como  
caracteres, es ```readlines()```.  

cuando el método ```readlines()```, se invoca sin argumentos, intenta **leer todo el**  
**contenido del archivo y devuelve una lista de cadenas, un elemento por línea del**  
**archivo**.  

Si no estás seguro de si el tamaño del archivo es lo suficientemente pequeño y no  
deseas probar el sistema operativo, puedes convencer al método ```readlines()``` de  
leer no más de un número especificado de bytes a la vez (el valor de retorno sigue  
siendo el mismo, es una lista de una cadena).  

Siéntete libre de experimentar con el siguiente código de ejemplo para entender cómo  
funciona el método ```readlines()```:  
```python
stream = open("text.txt")
print(stream.readlines(20))
print(stream.readlines(20))
print(stream.readlines(20))
print(stream.readlines(20))
stream.close()
```  

**El tamaño máximo del buffer de entrada aceptado se pasa al método como**  
**argumento**.  

Puedes esperar que ```readlines()``` procese el contenido de manera más  
efectiva que ```readline()```, ya que puede ser invocado menos veces.  

Nota: cuando no hay nada que leer del archivo, el método devuelve una lista vacía.  
Úsalo para detectar el final del archivo.  

Puedes esperar que al aumentar el tamaño del buffer mejore el rendimiento de entrada,  
pero no hay una regla de oro para ello: intenta encontrar los valores óptimos por ti  
mismo.  
<br></br>

Observa el código en el editor. Lo hemos modificado para mostrarte como usar  
```readlines()```.  
```python
from os import strerror

try:
    character_counter = line_counter = 0
    stream = open('text.txt', 'rt')
    lines = stream.readlines(20)
    while len(lines) != 0:
        for line in lines:
            line_counter += 1
            for char in line:
                print(char, end='')
                character_counter += 1
        lines = stream.readlines(10)
    stream.close()
    print("\n\nCaracteres en el archivo:", character_counter)
    print("Líneas en el archivo:     ", line_counter)
except IOError as e:
    print("Se produjo un error de E/S:", strerror(e.errno))
```  

Hemos decidido usar un buffer de 15 bytes de longitud. No puebses que es una  
recomendación.  

Hemos utilizado ese valor para evitar la situación en la que la primera invocación de  
```readlines()``` consuma todo el archivo.  

Queremos que el método se vea obligado a trabajar más duro y que demuestre sus  
capacidades.  

Existen **dos bucles anidados en el código**: el exterior emplea el resultado de  
```readlines()``` para iterar a través de el, mientras que el interno imprime las líneas  
carácter por carácter.  

<br></br>  


## **Procesando archivos de texto: continuación**  
El último ejemplo que queremos presentar muestra un rasgo muy interesante del objeto  
devuelto por la función ```open()``` en modo de texto.  

Creemos que puede sorprenderte: **el objeto es una instancia de la clase iterable**.  

Extraño? De ninguna manera. Usable? sí, por supuesto.  

El **protocolo de iteración definido para el objeto del archivo** es muy simple: su  
método ```__next__``` solo **devuelve la siguiente línea leída del archivo**.  

Además, puedes esperar que el objeto invoque automáticamente a ```close()``` cuando  
cualquiera de las lecturas del archivo lleguen al final del archivo.  

Mira el editor y ve cuan simple y claro se ha vuelto el código.  
```python
from os import strerror

try:
	character_counter = line_counter = 0
	for line in open('text.txt', 'rt'):
		line_counter += 1
		for char in line:
			print(char, end='')
			character_counter += 1
	print("\n\nCaracteres en el archivo: ", character_counter)
	print("Líneas en el archivo:     ", line_counter)
except IOError as e:
	print("Se produjo un error de E/S:", strerror(e.errno))
```  

<br></br>  


## **Manejando archivos de texto: *write()***  
Escribir archivos de texto parece ser más simple, ya que hay un método que puede  
usarse para realizar dicha tarea.  

El método se llama ```write()``` y espera solo un argumento: una cadena que se  
transferirá a un archivo abierto (no lo olvides), el modo de apertura debe reflejar la  
forma en que se transfieren los datos, **escribir en un archivo abierto en modo de**  
**lectura no tendrá éxito**.  

No se agrega carácter de nueva línea al argumento de ```write()```, por lo que debes  
agregarlo tu mismo si deseas que el archivo se complete con varias líneas.  

El ejemplo en el editor muestra un código muy simple que crea un archivo llamado  
*newtext.txt* (nota: el modo de apertura ```w``` asegura que **el archivo se creará desde**  
**cero**, incluso si existe y contiene datos) y luego coloca diez líneas en el.  
```python
from os import strerror

try:
	file = open('newtext.txt', 'wt') # Un nuevo archivo (newtext.txt) es creado.
	for i in range(10):
		s = "línea #" + str(i+1) + "\n"
		for char in s:
			file.write(char)
	file.close()
except IOError as e:
	print("Se produjo un error de E/S:", strerror(e.errno))
```  
<br></br>

La cadena que se grabará consta de la palabra línea, seguida del número de linea.  
Hemos decidido escribir el contenido de la cadena carácter por carácter (esto lo hace el  
bucle interno ```for```) pero no estás obligado a hacerlo de esta manera.  

Solo queríamos mostrarte que ```write()``` puede operar con caracteres individuales.  

El código crea un archivo con el siguiente texto:  
```
línea #1
línea #2
línea #3
línea #4
línea #5
línea #6
línea #7
línea #8
línea #9
línea #10
```  

Puedes imprimir el contenido del archivo en la consola?  

Te alentamos a que pruebes el comportamiento del método ```write()``` localmente en  
tu máquina.  

<br></br>  


## **Manejando archivos de texto: continuación**  
Mira el ejemplo en el editor. Hemos modificado el código anterior para escribir líneas  
enteras en el archivo de texto.  
```python
from os import strerror

try:
    file = open('newtext.txt', 'wt')
    for i in range(10):
        file.write("línea #" + str(i+1) + "\n")
    file.close()
except IOError as e:
    print("Se produjo un error de E/S:", strerror(e.errno))
```  

El contenido del archivo recién creado es el mismo.  

Nota: puedes usar el mismo método para escribir en el stream ```stderr```, pero no  
intentes abrirlo, ya que siempre está abierto implícitamente.  

Por ejemplo, si deseas enviar un mensaje de tipo cadena a ```stderr``` para distinguirlo de  
la salida normal del programa, puede verse así:  
```python
import sys
sys.stderr.write("Mensaje de Error")
```  

<br></br>  


## **Qué es un bytearray**?  
Antes de comenzar a hablar sobre archivos binarios, tenemos que informarte sobre una de las **clases**  
**especializadas que Python usa para almacenar datos amorfos**.  

**Los datos amorfos son datos que no tienen forma específica**, son solo una serie de bytes.  

Esto no significa que estos bytes no puedan tener su propio significado o que no puedan representar  
ningún objeto útil, por ejemlplo, gráficos de mapa de bits.  

El aspecto más importante de esto está en el sitio donde tenemos que contacto con los datos, no podemos, o simplemente no queremos, saber nada sobre ellos.  

Los datos amorfos no pueden almacenarse utilizando ninguno de los medios presentados  
anteriormente: no son cadenas ni listas.  

Debe haber un contenedor especial capaz de manejar dichos datos.  

Python tiene más de un contenedor, uno de ellos es **una clase especializada llamada bytearray**, como  
su nombre indica, es **un arreglo que contiene bytes (amorfos)**.  

Si deseas tener dicho contenedor, por ejemplo, para leer una imagen de mapa de bits y procesarla de  
alguna manera, debes crearlo explícitamente, utilizando uno de los constructores disponibles.  

Observa:  
```python
data = bytearray(10)
```  

Tal invocación crea un objeto bytearray capaz de almacenar diez bytes.  

Nota: dicho constructor **llena todo el arreglo con ceros**.  

<br></br>  


## **Bytearrays: continuación**  
Bytearrays se asemejan a listas en muchos aspectos. Por ejemplo, son **mutables**, son  
susceptibles a la función ```len()```, y puedes acceder a cualquiera de sus elementos  
usando indexación convencional.  

Existe una limitación importante: **no debes establecer ningún elemento del arreglo de**  
**bytes con un valor que no sea un entero** (violar esta regla causará una excepción  
*TypeError*) y tampoco está permitido **asignar un valor fuera del rango de 0 a 255** (a  
menos que quieras provocar una excepción *ValueError*).  

Puedes ** tratar cualquier elemento del arreglo de bytes como un valor entero**, al igual  
que en el ejemplo en el editor.  
```python
data = bytearray(10)

for i in range(len(data)):
    data[i] = 10 - i

for b in data:
    print(hex(b))
```  

Nota: hemos utilizado dos métodos para iterar el arreglo de bytes, y hemos utilizado la  
funcion ```hex()``` para ver los elementos impresos como valores hexadecimales.  

Ahora te vamos a mostrar **como escribir un arreglo de bytes en un archivo binario**,  
com no queremos guardar su representación legible, queremos escribir una copia uno a  
uno del contenido de la memoria física, byte a byte.  

<br></br>  


## **Bytearrays: continuación**  
Entonces, cómo escribimos un arreglo de bytes en un archivo binario?  

Observa el código en el editor.  
```python
from os import strerror

data = bytearray(10)

for i in range(len(data)):
    data[i] = 10 + i

try:
    binary_file = open('file.bin', 'wb')
    binary_file.write(data)
    binary_file.close()
except IOError as e:
    print("Se produjo un error de E/S:", strerror(e.errno))

# Ingresa aquí el código que lee los bytes del stream.
```  

Analicémoslo:  

- Primero, inicializamos ```bytearray``` con valores a partir de ```10```; si deseas que el  
contenido del archivo sea claramente legible, reemplaza el ```10``` con algo como  
```ord('a')```, esto producirá bytes que contienen valores correspondientes a la  
parte alfabética del código ASCII (no pienses que harás que un archivo sea un  
archivo de texto; sigue siendo binario, ya que se creó con un indicador: ```wb```).  

- Después, creamos el archivo usando la función ```open()```, la única diferencia en  
comparación con las variantes anteriores es que el modo de apertura contiene el  
indicador ```b```.  

- El método ```write()``` toma su argumento (```bytearray```) y lo envía (como un todo)  
al archivo.  

- El stream se cierra de forma rutinaria.  

El método ```write()``` devuelve la cantidad de bytes escritos correctamente.  

Si los valores difieren de la longitud de los argumentos del método, puede significar que  
hay algunos errores de escritura.  

En este caso, no hemos utilizado el resultado; esto puede no ser apropiado en todos los  
casos.  

Intenta ejecutar el código y analiza el contenido del archivo recién creado.  

Lo vas a usar en el siguiente paso.  

<br></br>  


## **Cómo leer bytes de un stream**  
La lecutra de un archivo binario requiere el uso de un método especializado llamado  
```readinto()```, ya que el método no crea un nuevo objeto del arreglo de bytes, sino que  
llena uno creado previamente con los valores tomados del archivo binario.  

Nota:  
- El método devuelve el número de bytes leídos con éxito.
- El método intenta llenar todo el espacio disponible dentro de su argumento; si  
existen más datos en el archivo que espacio en el argumento, la operación de  
lectura se detendrá antes del final del archivo; el resultado del método puede  
indicar que el arreglo de bytes solo se ha llenado de manera fragmentaria (el  
resultado también lo mostrará y la parte del arreglo que no está siendo utilizada  
por los contenidos recién leidos permanece intacta).  

Observa el código a continuación:  
```python
from os import strerror

data = bytearray(10)

try:
    binary_file = open('file.bin', 'rb')
    binary_file.readinto(data)
    binary_file.close()

    for b in data:
        print(hex(b), end=' ')
except IOError as e:
    print("Se produjo un error de E/S:", strerror(e.errno))
```  

Analicémoslo:  

- Primero, abrimos el archivo (el que se creó usando el código anterior) con el modo  
descrito como ```rb```.  

- Luego, leemos su contenido con el arreglo de bytes llamado ```data```, con un tamaño  
de diez bytes.  

- Finalmente, imprimimos el contenido del arreglo de bytes: Son los mismos que  
esperabas?  

Ejecuta el código y verifica si funciona.  

<br></br>  


## **Cómo leer bytes de un stream**  
Se ofrece una forma alternativa de leer el contenido de un archivo binario mediante el  
método denominado ```read()```.  

Invocado sin argumentos, intenta **leer todo el contenido del archivo en la memoria**,  
haciéndolo parte de un objeto recién creado de la clase bytes.  

Esta clase tiene algunas similitudes con ```bytearray```, con la excepción de una  
diferencia significativa: es **inmutable**.  

Afortunadamente, no hay obstaculos para crear un arreglo de bytes tomando su valor  
inicial directamente del objeto de bytes, como aquí:  
```python
from os import strerror

try:
    binary_file = open('file.bin', 'rb')
    data = bytearray(binary_file.read())
    binary_file.close()

    for b in data:
        print(hex(b), end=' ')

except IOError as e:
    print("Se produjo un error de E/S:", strerror(e.errno))
```  

Ten cuidado: **no utilices este tipo de lectura si no estás seguro de que el contenido**  
**del archivo se ajuste a la memoria disponible**.  

<br></br>  


## **Cómo leer bytes de un stream: continuación**  
Si el método ```read()``` se invoca con un argumento, **se especifica el número máximo**  
**de bytes a leer**.  

El método intenta leer la cantidad deseada de bytes del archivo, y la longitud del objeto  
devuelto puede usarse para determinar la cantidad de bytes realmente leídos.  

Puedes usar el método como aquí:  
```python
try:
    binary_file = open('file.bin', 'rb')
    data = bytearray(binary_file.read(5))
    binary_file.close()

    for b in data:
        print(hex(b), end=' ')

except IOError as e:
    print("Se produjo un error de E/S:", strerror(e.errno))
```  

Nota: los primeros cinco bytes del archivo han sido leídos por el código; los siguientes  
cinco todavía están esperando ser procesados.  

<br></br>  


## **Copiando archivos: una herramienta simple y funcional**  
Ahora vas a juntar todo este nuevo conocimiento, agregarle algunos elementos nuevos  
y usarlo para escribir un código real que pueda copiar el contenido de un archivo.  

Por supuesto, el propósito no es crear un reemplazo para los comandos como *copy* (de  
MS Windows) o cp (de Unix/Linux) pero para ver una forma posible de crear una  
herramienta de trabajo, incluso si nadie quiere usarla.  

Observa el código en el editor:  
```python
1  |from os import strerror
2  |
3  |source_file_name = input("Ingresa el nombre del archivo fuente: ")
4  |try:
5  |    source_file = open(source_file_name, 'rb')
6  |except IOError as e:
7  |    print("No se puede abrir archivo fuente: ", strerror(e.errno))
8  |    exit(e.errno)	
9  |
10 |destination_file_name = input("Ingresa el nombre del archivo destino: ")
11 |try:
12 |    destination_file = open(destination_file_name, 'wb')
13 |except Exception as e:
14 |    print("No se puede crear el archivo de destino:", strerror(e.errno))
15 |    source_file.close()
16 |    exit(e.errno)	
17 |
18 |buffer = bytearray(65536)
19 |total  = 0
20 |try:
21 |    readin = source_file.readinto(buffer)
22 |    while readin > 0:
23 |        written = destination_file.write(buffer[:readin])
24 |        total += written
25 |        readin = source_file.readinto(buffer)
26 |except IOError as e:
27 |    print("No se puede crear el archivo de destino: ", strerror(e.errno))
28 |    exit(e.errno)	
29 |    
30 |print(total,'byte(s) escritos con éxito')
31 |source_file.close()
32 |destination_file.close()
```  
Analicémoslo:  

- Las líneas 3 a la 8: solicitan al usuario el nombre del archivo a copiar e intentan  
abrirlo para leerlo; se termina la ejecución del programa si falla la apertura; nota:  
emplea la función ```exit()``` para detener la ejecución del programa y pasar el  
código de finalización al sistema operativo; cualquier código de finalización que no  
sea ```0``` significa que el programa ha encontrado algunos problemas; se debe  
utilizar el valor ```errno``` para especificar la naturaleza del problema.  

- Las líneas 10 a la 16: repiten casi la misma acción, pero esta vez para el archivo de salida.  

- La línea 18: prepara una parte de memoria para transferir datos del archivo fuente  
al destino; Tal área de transferencia a menudo se llama buffer, de ahi el nombre  
de la variable; el tamaño del buffer es arbitrario; en este caso decidimos usar  
64 KB; técnicamente, un buffer más grande es más rapido al copiar elementos,  
ya que un buffer más grande significa menos operaciones de E/S; en realidad,  
siempre hay un límite, cuyo cruce no genera más ventajas; pruébalo tú mismo si  
quieres.  

- Línea 19: cuenta los bytes copiados: este es el contador y su valor inicial.  

- Línea 21: intenta llenar el búfer por primera vez.  

- Línea 22: mientras se obtenga un número de bytes distinto a cero, repite las  
mismas acciones.  

- Línea 24: actualiza el contador.  

- Línea 25: lee el siguiente fragmento de archivo.  

- Las líneas 30 a la 32: limpieza final: el trabajo está hecho.  

<br></br>  


## **Puntos Clave**  
1. Para leer el contenido de un archivo, se pueden utilizar los siguientes métodos:  
- ```read(number)```: lee el ```número``` de carácteres/bytes del archivo y los retorna como una cadena, es  
capaz de leer todo el archivo a la vez.  
- ```readline()```: lee una sola línea del archivo de texto.  
- ```readlines(number)```: lee el ```número``` de líneas del archivo de texto; es capaz de leer todas las  
líneas a la vez.  
```readinto(bytearray)```: lee los bytes del archivo y llena del ```bytearray``` con ellos.  
<br></br>  

2. Para escribir contenido nuevo en un archivo, se pueden utilizar los siguientes métodos:  
- ```write(string)```: escribe una ```cadena``` a un archivo de texto.  
- ```write(bytearray)```: escribe todos los bytes de un ```bytearray``` a un archivo.  
<br></br>  

3. El método ```open()``` devuelve un objeto iterable que se puede usar para recorrer todas las líneas del  
archivo dentro de un bucle ```for```. Por ejemplo:  
```python
for line in open("file", "rt"):
    print(line, end='')
```  

El código copia el contenido del archivo a la consola, línea por línea. **Nota**: el stream se cierra  
**automáticamente** cuando llega al final del archivo.  

<br></br>  

#  
[Ejercicios](/Modulo4/Seccion3/Sec3-ej.md)
<br></br>

[Soluciones](/Modulo4/Seccion3/Sec3-ejsol.md)  

#

[Volver a: Módulo 4 - Miscelaneo](../README.md)

