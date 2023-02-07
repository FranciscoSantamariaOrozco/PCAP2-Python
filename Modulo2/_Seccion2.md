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