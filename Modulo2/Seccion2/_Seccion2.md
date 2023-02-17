## **Cadenas: una breve reseña**  
  
Hagamos un breve repaso de la naturaleza de las cadenas en Python.  
  
En primer lugar, las cadenas de Python (o simplemente cadenas, ya que no vamos a discutir las cadenas de  
ningún otro lenguaje) son **secuencias inmutables**.  
  
Es muy importante tener en cuenta esto, por que significa que debes esperar un comportamiento familiar.  
  
Analicemos el código en el editor para entender de lo qué estamos hablando:  
```
# Ejemplo 1

word = 'by'
print(len(word))


# Ejemplo 2

empty = ''
print(len(empty))


# Ejemplo 3

i_am = 'I\'m'
print(len(i_am))
```  
  
- Observa el **Ejemplo 1**. La función ```len()``` empleada en las cadenas devuelve el número de caracteres que  
contiene el argumento. La salida del código es ```2```.  
Cualquier cadena puede estar vacía. Si es el caso, su longitud es ```0``` como en el **Ejemplo 2**.  
  
- No olvides que la diagonal invertida (```\```) empleada como un carácter de escape, no esta incluida en la  
longitud normal de la cadena. El código en el **Ejemplo 3**, da como salida un ```3```.  
  
Ejecuta los tres ejemplos de código y verificalo.  
  
  
## **Cadenas multilínea**  
  
Ahora es un muy buen momento para mostrarte otra forma de especificar cadenas dentro del código fuente de  
Python. Ten en cuenta que la sintaxis que ya conoces no te permitirá usar una cadena que ocupe más de una  
línea de texto.  
  
Por esta razón, el código siguiente es erróneo:  
```
multiline = 'Línea #1
Línea #2'

print(len(multiline))
```  
  
Afortunadamente, para este tipo de cadenas, Python ofrece una sintaxis simple, conveniente y separada.  
  
Observa el código en el editor. Así es como se ve.  
```
multiline = '''Línea #1
Línea #2'''

print(len(multiline))
```  
  
Como puedes ver, la cadena comienza con **tres apóstrofes**, no uno. El mismo apóstrofe triplicado se usa para  
terminar la cadena.  
  
El número de lineas de texto dentro de una cadena de este tipo es arbitrario.  
  
La salida del código es ```17```.  
  
Cuenta los caracteres con cuidado. Es este resultado correcto o no? se ve bien a primera vista, pero cuando  
cuentas los caracteres, no lo es.  
  
```Linea #1``` contiene ocho caracteres. Las dos líneas juntas contienen 16 caracteres. Perdimos un carácter?  
Dónde? Cómo?  
  
No, no lo hicimos.  
  
**El carácter que falta es simplemente invisible: es un espacio en blanco**. Se encentra entre las dos líneas de texto.  
  
Se denota como: ```\n```.  
  
Lo recuerdas? es un carácter especial (de control) utilizado para **forzar un avance de línea**. No puedes verlo,  
pero cuenta.  
  
Las cadenas multilínea pueden ser delimitadas también por **comillas triples**, como aquí:  
```
multiline = """Línea #1
Línea #2"""

print(len(multiline))
```
  
Elige el método que sea más cómodo. Ambos funcionan igual.  
  
  
## **Operaciones con cadenas**  
  
Al igual que otros tiposde datos, las cadenas tienen su propio conjunto de operaciones permitidas, aunque son  
bastante limitadas en comparación con los números.  
  
En general, las cadenas pueden ser:  
  
- **Concatenadas** (unidas).  
- **Replicadas**.  
  
La primera operación la realiza el operador ```+``` (toma en cuenta que no es una adición o suma) mientras que la  
segunda por el operador ```*``` (toma en cuenta de nuevo que no es una multiplicación).  
  
La capacidad de usar el mismo operador en dos tipos de datos completamente diferentes (como números o  
cadenas) se llama **overloading - sobrecarga** (debido a que el operador está sobrecargado con diferentes tareas).  
  
Analiza el ejemplo:
```
str1 = 'a'
str2 = 'b'

print(str1 + str2)
print(str2 + str1)
print(5 * 'a')
print('b' * 4)
``` 
 
- El operador ```+``` es empleado en dos o más cadenas y produce una nueva cadena que contiene todos los  
caracteres de sus argumentos (nota: el orden es relevante aquí, en contraste con su versión numérica, la  
cual **es conmutativa**).  
  
- El operador ```*``` necesita una cadena y un número como argumentos; en este caso, el orden no importa:  
puedes poner el número antes de la cadena, o viceversa, el resultado será el mismo: una nueva cadena  
creada por la enésima replicación de la cadena del argumento.  
  
El fragmento de código produce el siguiente resultado:  
```
ab
ba
aaaaa
bbbb
```  
  
  
## **Operaciones con cadenas: *ord()***  
  
Si deseas **saber el valor del punto de código ASCII/UNICODE de un carácter específico**, puedes usar la  
función ```ord()``` (proveniente de *ordinal*).  
  
La función necesita **una cadena de un carácter como argumento** - incumplir este requisito provoca una  
excepción *TypeError*, y devuelve un número que representa el punto de código del argumento.  
  
```
# # Demostración de la función ord ().

char_1 = 'a'
char_2 = ' '  # space

print(ord(char_1))
print(ord(char_2))
```  

Observa el código en el editor y ejecútalo. La salida del fragmento de código es:  
  
```
97
32
```
  
Ahora asigna diferentes valores a ```ch1``` y ```ch2```, por ejemplo, ```α``` (letra griega alfa), y ```ę``` (una letra en el alfabeto  
polaco); luego ejecuta el código y ve qué resultado produce. Realiza tus propios experimentos.  
  
  
## **Operaciones con cadenas: *chr()***  
  
Si conoces el punto de código (número) y deseas obtener el carácter correspondiente, puedes usar la función  
llamada ```chr()```.  
  
La función **toma un punto de código y devuelve su carácter**.  
  
Invocándolo con un argumento inválido (por ejemplo, un punto de código negativo o inválido) provoca las  
excepciones *ValueError* o *TypeError*.  
  
```
# Demostración de la función chr.

print(chr(97))
print(chr(945))
```  
  
Ejecuta el código en el editor, su salida es la siguiente:  
```
a
α
```  
  
Nota:  
- ```chr(ord(x)) == x```
- ```ord(chr(x)) == x```  

De nuevo, realiza tus propios experimentos.  
  
  
## **Cadenas como secuencias: indexación**  
  
Ya dijimos antes que las **cadenas de Python son secuencias**. Es hora de mostrarte lo que significa realmente.  
  
Las cadenas no son listas, pero **pueden ser tratadas como tal en muchos casos**.  
  
Por ejemplo, si deseas acceder a cualquiera de los caracteres de una cadena, puedes hacerlo usando  
**indexación**. ejecuta el programa:
```
# Indexando cadenas.

the_string = 'silly walks'

for ix in range(len(the_string)):
    print(the_string[ix], end=' ')

print()
```  
  
Ten cuidado, no intentes pasar los límites de la cadena, ya que provocará una excepción.  
  
La salida del ejemplo es:  
  
```
s i l l y  w a l k s
```  
  
Por cierto, los índices negativos también se comportan como se espera. Comprueba esto tú mismo.  
  
  
## **Cadenas como secuencias: iterando**  
  
**El iterar a través de las cadenas**  funciona también. Observa el siguiente ejemplo:  
```
# Iterando a través de una cadena.

the_string = 'silly walks'

for character in the_string:
    print(character, end=' ')

print()
```  
  
La salida es la misma que el ejemplo anterior. Revísalo.  
  
  
## **Rebanadas**  
  
Todo lo que sabes sobre **rebanadas** es utilizable.  
  
Hemos reunido algunos ejemplos que muestran cómo funcionan las rebanadas en el mundo de las cadenas.  
Observa el código en el editor, analízalo y ejecútalo.  
```
# Rebanadas

alpha = "abdefg"

print(alpha[1:3])
print(alpha[3:])
print(alpha[:3])
print(alpha[3:-2])
print(alpha[-3:4])
print(alpha[::2])
print(alpha[1::2])
```
  
No verás nada nuevo en el ejemplo, pero queremos que estés seguro de entender todas las líneas del código.  
  
La salida del código es:
```
bd
efg
abd
e
e
adf
beg
```  
  
Ahora haz tus propios experimentos.  
  
  
## **Los operadores *in* y *not in***  
  
### El operador *in*  
  
El operador ```in```  
  
El operador ```in``` no debería sorprenderte cuando se aplica a cadenas, simplemente **comprueba si el**  
**argumento izquierdo (una cadena) se puede encontrar en cualquier lugar dentro del argumento derecho**  
**(otra cadena).**  
  
El resultado es simplemente ```True(Verdadero)``` o ```False(Falso)```.  
  
Observa el ejemplo a continuación. Así es como el operador ```in``` funciona:  
```
alphabet = "abcdefghijklmnopqrstuvwxyz"

print("f" in alphabet)
print("F" in alphabet)
print("1" in alphabet)
print("ghi" in alphabet)
print("Xyz" in alphabet)
```  
  
La salida del ejemplo es:  
```
True
False
False
True
False
```  
  
### **El operador** *not in*  
  
Como probablemente puedas deducir, el operador ```not in``` también es aplicable aquí.  
  
Así es como funciona:  
```
alphabet = "abcdefghijklmnopqrstuvwxyz"

print("f" not in alphabet)
print("F" not in alphabet)
print("1" not in alphabet)
print("ghi" not in alphabet)
print("Xyz" not in alphabet)
```  
  
La salida del ejemplo es:  
```
False
True
True
False
True
```  
  
  
## **Las cadenas de Python son inmutables**  
  
También te hemos dicho que las **cadenas de Python son inmutables**.  Esta es una característica muy  
importante. Qué significa?  
  
Esto significa principalmente que la similitud de cadenas y listas es limitada. No todo lo que puede hacerse con una lista puede hacerse con una cadena.  
  
La primera diferencia importante **no te permite usar la instrucción ```del``` para eliminar cualquier cosa de**  
**una cadena**  
  
El ejemplo siguiente no funcionará:  
```
alphabet = "abcdefghijklmnopqrstuvwxyz"
del alphabet[0]
```  
  
Lo único que puedes hacer con ```del``` y una cadena es **eliminar la cadena como un todo**. Intenta hacerlo.  
  
Las cadenas de PYthon **no tienen el método** ```append()``` - no se pueden expandir de ninguna manera.  
  
El siguiente ejemplo es erróneo:  
```
alphabet = "abcdefghijklmnopqrstuvwxyz"
alphabet.append("A")
```  
  
Con la ausencia del método ```append()``` **el método** ```insert()``` también es ilegal:
```
alphabet = "abcdefghijklmnopqrstuvwxyz"
alphabet.insert(0, "A")
```  
  
  
## **Operaciones con cadenas: continuación**  
  
No pienses que la inmutabilidad de una cadena limita tu capacidad de operar con ellas.  
  
La única consecuencia es que debes recordarlo e implementar tu código de una manera ligeramente diferente:  
Observa el código en el editor.
```
alphabet = "bcdefghijklmnopqrstuvwxy"

alphabet = "a" + alphabet
alphabet = alphabet + "z"

print(alphabet)
```  
  
Esta forma de código es totalmente aceptable, funcionará sin doblar las reglas de Python y traerá el alfabeto  
latino completo a tu pantalla:  
```
abcdefghijklmnopqrstuvwxyz
```  
  
Es posible que desees preguntar si el **crear una nueva copia de una cadena cada vez que se modifica su**  
**contenido empeora la efectividad del código**.  
  
Sí lo hace un poco. Sin embargo, no es un problema en lo absoluto.  
  
    
## **Operaciones con cadenas: *min()***  
  
Ahora que comprendes que las cadenas son secuencias, podemos mostrarte algunas capacidades de secuencia  
menos obvias. Las presentaremos utilizando cadenas, pero no olvides que las listas también pueden adoptar los  
mismos trucos.  
  
Comenzaremos con la función llamada ```min()```.  
  
Esta función **encuentra el elemento mínimo de la secuencia pasada como argumento**.  Existe una condición -  
la seecuencia (cadena o lista) **no puede estar vacía**, de lo contrario obtendrás una excepción *ValueError*.  

```
# Demonstrando min() - Ejemplo 1:
print(min("aAbByYzZ"))


# Demonstrando min() - Ejemplo 2 y 3:
t = 'Los Caballeros Que Dicen "¡Ni!"'
print('[' + min(t) + ']')

t = [0, 1, 2]
print(min(t))
```   
  
El programa Ejemplo 1 da la siguiente salida:  
```
A
```  
  
Nota: es una A mayúscula. Por qué? Recuerda la tabla ASCII, qué letras ocupan las primeras posiciones,  
mayúsculas o minúsculas?  
  
Hemos preparado dos ejemplos más para analizar: **Ejemplos 2 y 3**.  
  
Como puedes ver, presentan más que solo dos cadenas. El rsultado esperado se ve de la siguiente manera:  
```
[ ]
0
```  
  
Nota: hemos utilizado corchetes para evitar que el espacio se pase por alto en tu pantalla.  
   

## **Operaciones con cadenas: *max()***  
  
Del mismo modo, una función llamada ```max()``` **encuentra el elemento máximo de la secuencia**.  
```
# Demostración de max() - Ejemplo 1:
print(max("aAbByYzZ"))


# Demostración de max() - Ejemplo 2 & 3:
t = 'Los Caballeros Que Dicen "¡Ni!"'
print('[' + max(t) + ']')

t = [0, 1, 2]
print(max(t))
```  
  
Observa el **Ejemplo 1** en el editor. La salida del programa es:
```
z
```  
  
Nota: es una z minúscula.  
  
Ahora veamos la función ```max()``` a los mismos datos del ejemplo anterior. Observa los **Ejemplos 2 y 3** en el  
editor.  
  
La salida esperada es:
```
[¡]
2
```  
  
Realiza tus propios experimentos.  
  

## **Operaciones con cadenas: el método *index()***  
  
El método ```index()``` (es un método, no una función) **busca la secuencia desde el principio, para encontrar el**  
**primer elemento del valor especificado en su argumento**.  
 
Nota: el elemento buscado debe aparecer en la secuencia - **su ausencia causará una excepción *ValueError***.  
  
El método devuelve el **índice de la primera aparición del argumento** (lo que significa que el resultado más  
bajo posible es *0*, mientras que el más alto es la longitud del argumento decrementado en 1).  
```
# Demonstrando el método index():
print("aAbByYzZaA".index("b"))
print("aAbByYzZaA".index("Z"))
print("aAbByYzZaA".index("A"))
```
  
Por lo tanto, el ejemplo en la salida del editor es:
```
2
7
1
```  
  

## **Operaciones con cadenas: la función *list()***  

La función ```list()``` **toma su argumento (ujna cadena) y crea uina nueva lista que contiene todos los**  
**caracteres de la cadena, uno por elemento de la lista.**  
  
Nota: no es estrictamente una función de cadenas - ```list()``` es capaz de crear una nueva lista de muchas  
otras entidades (por ejemplo, de tuplas  y diccionarios).  
  
Observa el código de ejemplo en el editor.
```
### Demostración de la función list():
print(list("abcabc"))

# Demostración de la función list():
print("abcabc".count("b"))
print('abcabc'.count("d"))
```  
  
La salida es:
```
['a', 'b', 'c', 'a', 'b', 'c']
```  
  
  
## **Operaciones con cadenas: el método *count()***  
  
El método ```count()``` **cuenta todas las apariciones del elemento dentro de la secuencia**. La ausencia de tal  
elemento no causa ningún problema.  
  
Observa el segundo ejemplo en el editor. Puedes adivinar su salida?  
  
Es:  
```
2
0
```  
  
Las cadenas de Python tienen un número significativo de métodos destinados exclusivamente al procesamiento  
de caracteres. No esperes que trabajen con otras colecciones. La lista completa se presenta aquí:  
[https://docs.python.org/3.4/library/stdtypes.html#string-methods](https://docs.python.org/3.4/library/stdtypes.html#string-methods)  
  
Te mostraremos los que consideramos más útiles.  
  

## **Puntos Claves**  

1. Las cadenas de Python **son secuencias inmutables** y se pueden indexar, dividir en rebanadas e iterar como cualquier otra  
secuencia, además de estar sujetas a los operadores ```in``` y ```not in```. Existen dos tipos de cadenas en Python:  
  
- Cadenas de **una línea**, las cuales no pueden cruzar los límites de una linea, las denotamos usando apóstrofes (```'cadena'```) o  
comillas (```"cadena"```).  
- Cadenas **multilínea**, que ocupan más de una línea de código fuente, delimitadas por apóstrofes triples:
```
'''
cadena
'''
```
  
o  
```
"""
cadena
"""
```  
  
2. La longitud de una cadena está determinada por la función ```len()```. El carácter de escape (```\```) no es contado. Por ejemplo:
```
print(len("\n\n"))
```  
  
Su salida es ```2```.  
  
  
3. Las cadenas pueden ser **concatenadas** usando el operador ```+```, y **replicadas** usando el operador ```*```. Por ejemplo:  
  
```
asterisk = '*'
plus = "+"
decoration = (asterisk + plus) * 4 + asterisk
print(decoration)
```  
  
Salida ```*+*+*+*+*```  
  

4. El par de funciones ```chr()``` y ```ord()``` se pueden utilizar para crear un carácter utilizando su punto de código y para determinar un  
punto de código correspondiente a un carácter. Las dos expresiones siguientes son siempre verdaderas:  
```
chr(ord(character)) == character
ord(chr(codepoint)) == codepoint
```  
  
  
5. Algunas otras funciones que se pueden aplicar a cadenas son:
  
- ```list()``` -> Crea una lista que consta de todos los caracteres de la cadena.  
- ```max()``` -> Encuentra el carácter con el punto de código máximo.  
- ```min()``` -> Encuentra el carácter con el punto de código mínimo.  
  
  
6. El método llamado ```index()``` encuentra el índice de una subcadena dada dentro de la cadena.