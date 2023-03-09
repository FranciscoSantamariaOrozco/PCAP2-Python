## **Errores, fallas y otras plagas**  
**Cualquier cosa que pueda salir mal, saldrá mal.**  

Esta es la ley de Murphy, y funciona en todo y siempre. Si la ejecución del código puede  
salir mal, lo hará.  

Observa el código en el editor. Hay almenos dos formas posibles de que "salga mal" la  
ejecución. Puedes verlas?
```
import math

x = float(input("Ingresa x: "))
y = math.sqrt(x)

print("La raíz cuadrada de", x, "es igual a", y)
```

- Como el usuario puede ingresar una cadena de caracteres completamente arbitraria, **no hay garantía de**  
**que la cadena se pueda convertir en un valor floante**: esta es la primera vulnerabilidad del código.  
- La segunda es que la función ```sqrt()``` **fallará si se le ingresa un valor negarivo**.  


Puedes recibir alguno de los siguientes mensajes de error.  

Algo como esto:
```
Ingresa x: Abracadabra

Traceback (most recent call last):

  File "sqrt.py", line 3, in <module>

    x = float(input("Ingresa x: "))

ValueError: could not convert string to float: 'Abracadabra'
```  

O algo como esto:
```
Ingresa x: -1

Traceback (most recent call last):

  File "sqrt.py", line 4, in <module>

    y = math.sqrt(x)

ValueError: math domain error
```  

Puedes protegerte de tales sorpresas? Por supuesto. Además, tienes que hacerlo para ser considerado un  
buen programador.  

<br></br>


## **Excepciones**  
Cada vez que tu código intenta hacer algo erróneo, irresponsable o inaplicable, Python hace dos cosas:  

- **Detiene tu programa**.
- Crea un tipo especial de dato, llamado **excepción**.  

Ambas actividades llevan por nombre **generar una excepción**. Podemos decir que Python siempre genera una excepción (o que una  
**excepción ha sido generada**) cuando no tiene ni idea de qué hacer con el código.  

Qué ocurre depués?  

- La excepción generada espera que alguien o algo lo note y haga algo al respecto.
- Si la excepción no es resuelta, el programa será **terminado abruptamente**, y verás un **mensaje de error** enviado a la consola  
por PYthon.
- De otra manera, si se atiende la excepción y es **manejada** apropiadamente, el programa puede reanudarse y su ejecución puede  
continuar.  

Python proporciona herramientas efectivas que permiten **observar, identificar y manejar las excepciones** eficientemente. Esto es  
posible debido a que todas las excepciones potenciales tienen un nombre específico, por lo que se pueden clasificar y reaccionar a  
ellas adecuadamente.  

Ya conoces algunos nombres de las excepciones. Observa el siguiente mensaje de diagnóstico:  
```
ValueError: math domain error
```  

La palabra "ValueError" es el **nombre de la excepción**. Vamos a familiarizarnos con algunas otras excepciones.  

<br></br>


## **Excepciones: continuación**  
Observa el código en el editor. Ejecuta el (obviamente incorrecto) programa.
```
Evalue = 1
value /= 0
```  

Verás el siguiente mensaje en respuesta:  
```
Traceback (most recent call last):
File "div.py", line 2, in 
value /= 0
ZeroDivisionError: division by zero
```  

Este error es llamado ***ZeroDivisionError***.  

<br></br>


## **Excepciones: continuación**  
Observa el código en el editor. Qué pasará cuando lo ejecutes? revísalo.
```
my_list = []
x = my_list[0]
```  

Verás el siguiente mensaje en respuesta:
```
Traceback (most recent call last):
File "lst.py", line 2, in 
x = list[0]
IndexError: list index out of range
```  

Este es el *IndexError* (error de índice).  

<br></br>


## **Excepciones: continuación**  
Cómo se **manejan** las excepciones? La palabra ```try``` es clave para la solución.  

Además, también es una palabra clave reservada.  

La receta para el éxito es la siguiente:  

- Primero, se debe ***intentar (try)* hacer algo**.  
- Después, tienes que **comprobar si todo salió bien**.  

Pero, no sería mejor verificar primero todas las circunstancias y luego hacer algo solo si es seguro?  

Justo como en el ejemplo en el editor.  
```
first_number = int(input("Ingresa el primer numero: "))
second_number = int(input("Ingresa el segundo numero: "))

if second_number != 0:
    print(first_number / second_number)
else:
    print("Esta operación no puede ser realizada.")

print("FIN.")
```  

Es cierto que esta forma puede parecer la mas natural y comprensible, pero en realidad, este método no facilita  
la programación. Todas estas revisiones pueden hacer **al código demasiado grande e ilegible**.  

Python prefiere un enfoque completamente diferente.  

<br></br>


## **Excepciones: continuación**  
Observa el código en el editor. Este es el enfoque favorito de Python.  
```
first_number = int(input("Ingresa el primer numero: "))
second_number = int(input("Ingresa el segundo numero: "))

try:
    print(first_number / second_number)
except:
    print("Esta operación no puede ser realizada.")

print("FIN.")
```  

Nota:  

- La palabra reservada ```try``` **comienza con un bloque de código** el cual puede o no estar funcionando  
correctamente.  
- Después, Python intenta realizar la acción arriesgada: si falla, se genera una excepción y Python comienza  
a buscar una solución.  
- La palabra reservada ```except``` comienza con un bloque de código que será **ejecutado si algo dentro del**  
**bloque** ```try``` **sale mal**: si se genera una excepción dentro del bloque anterrior ```try```, **fallará aquí**,  
entonces el código ubicado después de la palabra clave reservada except debería proporcionar una  
**reacción adecuada** a la excepción planteada.  
- Por ultimo, se regresa al nivel de anidación anterior, es decir, se termina la sección **try-except**.  

Ejecuta el código y prueba su comportamiento.  

Resumamos esto:  

```
try:
    :
    :
except:
    :
    :
```  

- En el primer paso, Python intenta realizar todas las instrucciones colocadas entre las instrucciones ```try:```  
y ```except:```.  
- Si no hay ningún problema con la ejecución y todas las instrucciones se realizan con éxito, la ejecución  
salta al punto después de la última línea del bloque ```except:```, y la ejecución del bloque se considera  
completa.  
- Si algo sale mal dentro del bloque ```try:``` o ```except:```, la ejecución salta inmediatamente fuera del bloque  
y entra en la primera instrucción ubicada después de la palabra clave reservada ```except:```, esto significa  
que algunas de las instrucciones del bloque pueden ser silenciosamente omitidas.  

<br></br>


## **Excepciones: continuación**  
Observa el código en el editor. Te ayudará a comprender este mecanismo.
```
try:
    print("1")
    x = 1 / 0
    print("2")
except:
    print("Oh cielos, algo salió mal...")

print("3")
```  

Esta es la salida que produce:  
```
1
Oh cielos, algo salió mal...
3
```  

Nota: la instrucción ```print("2")```, se perdió en el proceso.  

<br></br>


## **Excepciones: continuación**  
Este enfoque tiene una desventaja importante: si existe la posibilidad de que más de una excepción se salte a  
un apartado ```except:```, puedes tener **problemas para descubrir lo que realmente sucedió**.  

Al igual que en el código en el editor. Ejecútalo y ve lo que pasa.  
```
try:
    x = int(input("Ingresa un numero: "))
    y = 1 / x
except:
    print("Oh cielos, algo salió mal...")

print("FIN.")
```

El mensaje ```Oh cielos, algo salio mal...``` que aparece en la consola no dice nada acerca de la razón,  
mientras que hay dos posibles causas de la excepción:  

- Datos no enteros fueron ingresados por el usuario.
- un valor entero igual a ```0``` fue asignado a la variable ```x```.  

Técnicamente, hay dos formas de resolver el problema:  

- Construir dos bloques consecutivos *try-except*, uno por cada posible motivo de excepción (fácil, pero  
provocará un crecimiento desfavorable del código). 
- Emplear una variante más avanzada de la instrucción.  

Se ve de la siguiente manera:
```
try:
    :
except exc1:
    :
except exc2:
    :
except:
    :
```  

Así es como funciona:

- Si el ```try``` genera la excepción ```exc1```, esta será manejada por el bloque ```except exc1:```.
- De la misma manera, si el ```try``` genera la excepción ```exc2```, esta será manejada por 
el bloque ```except exc2:```.
- Si el ```try``` genera cualquier otra excepción, será manejado por el bloque sin nombre ```except```.

Pasemos a la siguiente parte del curso y veámoslo en acción.  

<br></br>


## **Excepciones: continuación**  
Observa el código en el editor. Nuestra solución esta ahí.  
```
try:
    x = int(input("Ingresa un numero: "))
    y = 1 / x
    print(y)
except ZeroDivisionError:
    print("No puedes dividir entre cero, lo siento.")
except ValueError:
    print("Debes ingresar un valor entero.")
except:
    print("Oh cielos, algo salió mal...")

print("FIN.")
```

El código, cuando se ejecute, producirá una de las siguientes cuatro variantes de salida:  

- Si se ingresa un valor entero válido distinto de cero (por ejemplo, ```5```) dirá:
```
0.2
FIN.
```  

- Si se ingresa ```0```, dirá:
```
No puedes dividir entre cero, lo siento.
FIN.
```

- Si se ingresa cualquier cadena no entera, verás:
```
Debes ingresar un valor entero.
FIN.
```

- (Localmente en tu máquina) si presionas Ctrl+C mientras el programa está esperando la entrada del usuario  
(provocará una excepción denominada *KeyboardInterrupt*), el programa dirá:  
```
Oh cielos, algo salió mal...
FIN.
```  

<br></br>


## **Excepciones: continuación**  
No olvides que:  

- Los bloques ```except``` son analizados en el mismo orden en que aparecen en el código.
- No debes usar más de un bloque de excepción con el mismo nombre.
- El número de diferentes bloques ```except``` es arbitrario, la única condición es que si se emplea el ```try```, 
debes poner almenos un ```except``` (nombrado o no) después de el.
- La palabra clave reservada ```except``` no debe ser empleada sin que le preceda un ```try```.  
- Si uno de los bloques ```except``` es ejecutado, ningún otro lo será.  
- Si ninguno de los bloques ```except``` especificados coincide con la excepción planteada, la excepción  
permanece sin manejar (lo discutiremos pronto).  
- Si un ```except``` sin nombre existe, tiene que especificarse como el último.  
```
try:
    :
except exc1:
    :
except exc2:
    :
except:
    :
```  

Continuemos ahora con los experimentos.  

Observa el código en el editor. Hemos modificado el programa anterior, hemos eliminado el bloque  
```ZeroDivisionError```.  

Qué sucede ahora si el usuario ingresa un ```0``` como entrada?  

Como no existe un **bloque declarado** para la división entre cero, la excepción cae dentro del bloque **general**  
**(sin nombre)**: esto significa que en este caso, el programa dirá:  
```
Oh cielos, algo salió mal...
FIN.
```  

Inténtalo tu mismo. Ejecuta el programa.  

<br></br>


## **Excepciones: continuación**  
Echemos a perder el código una vez más. 

Observa el programa en el editor. Esta vez, hemos eliminado el bloque sin nombre.  
```
try:
    x = int(input("Ingresa un número: "))
    y = 1 / x
    print(y)
except ValueError:
    print("Debes ingresar un valor entero.")

print("FIN.")
```  

El usuario ingresa nuevamente un ```0```, y:  

- La excepción no será manejada por ```ValueError```: no tiene nada que ver con ello.  
- Como no hay otro bloque, deberías ver este mensaje:  
```
Traceback (most recent call last):
File "exc.py", line 3, in 
y = 1 / x
ZeroDivisionError: division by zero
```  

Has aprendido mucho sobre el manejo de excepciones en Python. En la siguiente sección, nos centraremos en  
las excepciones integradas de Python y sus jerarquías.  

<br></br>


## **Puntos Clave**  
1. Una excepción es un evento durante la ejecución del programa causado por una situación anormal. La excepción debe manejarse  
para evitar la terminación del programa. La parte del código que se sospecha que es la fuente de la excepción debe colocarse dentro  
del bloque ```try```.  
Cuando ocurre la excepción, la ejecución del código no se termina, sino que salta al bloque ```except```. Este es el lugar donde debe  
llevarse a cabo el manejo de la excepción. El esquema general para tal construcción es el siguiente:  
```
:
# El código que siempre corre suavemente.
:
try:
    :
    # Código arriesgado.
    :
except:
    :
    # La gestión de la crisis se lleva a cabo aquí.
    : 
:
# De vuelta a la normalidad.
:
```  
<br></br>

2. Si necesitas manejar más de una excepción proveniente del mismo bloque ```try```, puedes agregar más de un bloque ```except```,  
pero debes etiquetarlos con diferentes nombres, así:  
```
:
# El código que siempre corre suavemente.
:
try:
    :
    # Código arriesgado.
    :
except Except_1:
    # La gestión de la crisis se lleva a cabo aquí.
except Except_2:
    # Salvamos el mundo aqui.
:
# De vuelta a la normalidad.
:
```  

En el mejor caso, se ejecuta uno de los bloques ```except```; ninguno de los bloques se ejecuta cuando la excepción generada no  
coincide con ninguna de las excepciones especificadas.  
<br></br>

3. No se puede agregar más de un bloque de ```excepción sin nombre``` después de los bloques con nombre.  
```
:
# El código que siempre corre suavemente.
:
try:
    :
    # Código arriesgado.
    :
except Except_1:
    # La gestión de la crisis se lleva a cabo aquí.
except Except_2:
    # Salvamos el mundo aqui.
except:
    # Todos los demás problemas caen aquí.
:
# De vuelta a la normalidad.
:
```  


<br></br>  


#  
[Ejercicios](Sec6-ej.md)
<br></br>

[Soluciones](Sec6-ejsol.md)  

#

[Volver a: Módulo 2 - Cadenas, métodos de listas y excepciones](../README.md)