## **Excepciones**  
Python 3 define **63 excepciones integradas**, y todas ellas forman una **jerarquía en forma de árbol**, aunque el árbol es un poco  
extraño ya que su raíz se encuentra en la parte superior.  

Algunas de las excepciones integradas son más generales (incluyen otras excepciones) mientras que otras son completamente  
concretas (solo se representan a sí mismas). Podemos decir que **cuanto más cerca de la raíz se encuentra una excepción, más**  
**general (abstracta) es**. A su vez, las excepciones ubicadas en los extremos del árbol (podemos llamarlas **hojas**) son concretas.  

Observa la figura:  

<p align="center">
<img src="img/exceptionstree.jpg">
</p>  

Muestra una pequeña sección del árbol completo de excepciones. Comencemos examinando el árbol desde la hoja  
*ZeroDivisionError*.  

Nota:  

- *ZeroDivisionError* es un caso especial de una clase de excepción más general llamada *ArithmeticError*.  
- *ArithmeticError* es un caso especial de una clase de excepción más general llamada solo *Exception*.  
- *Exception* es un caso especial de una clase más general llamada *BaseException*.  

Podemos describirlo de la siguiente manera (observa la dirección de las flechas; siempre apuntan a la entidad más general):  

<p align="center">
<img src="img/exceptionsjerarchy.jpg">
</p>  

Te mostraremos el funcionamiento de esta generalización. Comencemos con un código realmente simple.  

<br></br>


## **Excepciones: continuación**  
Observa el código en el editor. Es un ejemplo simple para comenzar. Ejecútalo.  
```
try:
    y = 1 / 0
except ZeroDivisionError:
    print("Uuupsss...")

print("FIN.")
```  

La salida que esperamos ver es la siguiente:  
```
Uuuppsss...
FIN.
```  

Ahora observa el código a continuación:  
```
try:
    y = 1 / 0
except ArithmeticError:
    print("Uuuppsss...")

print("FIN.")
```  

Algo ha cambiado: hemos reemplazado ```ZeroDivisionError``` con ```ArithmeticError```  

Ya se sabe que ```ArithmeticError``` es una clase general que incluye (entre otras) la excepción  
```ZeroDivisionError```.  

Por lo tanto, la salida del código permanece sin cambios. Pruébalo.  

Esto también significa que reemplazar el nombre de la excepción ya sea con ```Exception``` o ```BaseException```  
no cambiará el comportamiento del programa.  

Vamos a resumir:  

- Cada excepción generada **cae en la primer coincidencia**. 
- La coincidencia correspondiente no tiene que especificar exactamente la misma excepción, es suficiente  
que la excepción sea **más general** (más abstracta) que la generada.  

<br></br>


## **Excepciones: continuación**  
Observa el código en el editor. Qué pasará aquí?  
```
try:
    y = 1 / 0
except ZeroDivisionError:
    print("¡División entre Cero!")
except ArithmeticError:
    print("¡Problema Aritmético!")

print("FIN.")
```  

La primera coincidencia es la que contiene ```ZeroDivisionError```. Significa que la consola mostrará:  
```
¡División entre Cero!
FIN.
```  

Cambiará algo si intercambiamos los dos bloques ```except```? Justo como aquí abajo:  

```
try:
    y = 1 / 0
except ArithmeticError:
    print("¡Problema Aritmético!")
except ZeroDivisionError:
    print("¡División entre Cero!")

print("FIN.")
```

El cambio es radical: la salida del código es ahora:  

```
¡Problema Aritmético!
FIN.
```  

Por qué, si la excepción generada es la misma que antes?  

La excepción es la misma, pero la excepción más general ahora aparece primero: también capturará todas las  
divisiones entre cero. También significa que no hay posibilidad de que alguna excepción llegue a  
*ZeroDivisionError*. Ahora es completamente inalcanzable.  

Recuerda:  

- El orden de las excepciones importa!  
- No pongas excepciones más generales antes que otras más concretas.  
- Esto hará que el último sea inalcanzable e inútil.  
- Además, hará que el código sea desordenado e inconsistente.  
- Python no generará ningún mensaje de error con respecto a este problema.  

<br></br>


## **Excepciones: continuación**  
Si deseas **manejar dos o más excepciones** de la misma manera, puedes usar la siguiente sintaxis:  
```
try:
    :
except (exc1, exc2):
    :
```  

Simplemente tienes que poner todos los nombres de las excepciones empleadas en una lista separada por  
comas y no olvidar los paréntesis.  

Si una **excepción es generada dentro de una función**, puede ser manejada:  

- Dentro de la función.
- Fuera de la función.

Comencemos con la primera variante: observa el código en el editor.  

La excepción *ZeroDivisionError* (la cual es un caso concreto de la clase *ArithmeticError*) es generada  
dentro de la función ```badfun()```, y la función en sí misma se encarga de ella.  

La salida del programa es:  
```
¡Problema Aritmético!
FIN.
```  

También es posible dejar que la excepción se propague **fuera de la función**. Probémoslo ahora.  

Observa el código a continuación:  
```
def bad_fun(n):
    return 1 / n

try:
    bad_fun(0)
except ArithmeticError:
    print("¿Que pasó? ¡Se generó una excepción!")

print("FIN.")
```  

El problema tiene que ser resuelto por el invocador (o por el invocador del invocador, y así sucesivamente).  

La salida del programa es:  
```
¿Qué pasó? ¡Se generó una excepción!
FIN.
```  

Nota: la **excepción generada puede cruzar la función y los límites del módulo**, y viajar a través de la cadena  
de invocación buscando una cláusula ```except``` capaz de manejarla.  

Si no existe tal cláusula, la excepción no se controla y Python resuelve el problema de la manera estándar -  
**terminando el código y emitiendo un mensaje de diagnóstico**.  

Ahora vamos a suspender esta discusión, ya que queremos presentarte una nueva instrucción de Python.  

<br></br>


## **Excepciones: continuación**  
La instrucción ```raise``` genera la excepción especificada denominada ```exc``` como si fuese generada de manera  
natural:
```raise exc```  

Nota: ```raise``` es una palabra clave reservada.  

La instrucción te permite:  

- **Simular excepciones reales** (por ejemplo, para probar tu estrategia de manejo de excepciones).
- Parcialmente **manejar una excepción** y hacer que otra parte del código sea responsable de completar el  
manejo.  

Observa el código en el editor. Así es como puedes usarlo en la práctica.  
```
def bad_fun(n):
    raise ZeroDivisionError


try:
    bad_fun(0)
except ArithmeticError:
    print("¿Que pasó? ¿Un error?")

print("FIN.")
```

La salida del programa permanece sin cambios.  

De esta manera, puedes **probar tu rutina de manejo de excepciones** sin forzar al código a hacer cosas  
incorrectas.  

<br></br>


## **Excepciones: continuación**  
La instrucción ```raise``` también se puede utilizar de la siguiente manera (toma en cuenta la ausencia del nombre  
de la excepción):  
```
raise
```  

Existe una seria restricción: esta variante de la instrucción ```raise``` puede ser utilizada **solamente dentro del**  
**bloque** ```except```; usarla en cualquier otro contexto causa un error.  

La instrucción volverá a generar la misma excepción que se maneja actualmente.  


Gracias a esto, puedes distribuir el manejo de excepciones entre diferentes partes del código.  

Observa el código en el editor. Ejecútalo, lo veremos en acción.  
```
def bad_fun(n):
    try:
        return n / 0
    except:
        print("¡Lo hice otra vez!")
        raise


try:
    bad_fun(0)
except ArithmeticError:
    print("¡Ya veo!")

print("FIN.")
```

La excepción *ZeroDivisionError* es generada dos veces:  

- Primero, dentro del ```try``` debido a que se intentó realizar una división entre cero.  
- Segundo, dentro de la parte ```except``` por la instrucción ```raise```.  

En efecto, la salida del código es:
```
¡Lo hice otra vez!
¡Ya veo!
FIN.
```  

<br></br>


## **Excepciones: continuación**  
Ahora es un buen momento para mostrarte otra instrucción de Python, llamada ```assert``` (afirmar). Esta es una  
palabra clave reservada.  
```
assert expression
```  

Cómo funciona?

- Se evalúa la expresión.
- Si la expresión se evalúa como ```True``` (verdadera), o un valor numérico distinto de cero, o una cadena no  
vacía, o cualquier otro valor diferente de ```None```, no hará nada más.  
- De lo contrario, automáticamente e inmediatamente se genera una excepción llamada *AssertionError*  
(en este caso, decimos que la afirmación ha fallado).  

Cómo puede ser utilizada?  

- Puedes ponerlo en la parte del código donde quieras estar **absolutamente a salvo de datos incorrectos**,  
y donde no estés absolutamente seguro de que los datos hayan sido examinados cuidadosamente antes  
(por ejemplo, dentro de una función utilizada por otra persona).  
- El generar una excepción *AssertionError* asegura que tu código no produzca resultados no válidos y  
muestra claramente la naturaleza de la falla.  
- **Las aserciones no reemplazan las excepciones ni validan los datos**, son suplementos.  

Si las excepciones y la validación de datos son como conducir con cuidado, la aserción puede desempeñar el  
papel de una bolsa de aire.  

Veamos a la instrucción ```assert``` en acción. Observa el código en el editor. Ejecútalo.  
```
import math

x = float(input("Ingresa un número: "))
assert x >= 0.0

x = math.sqrt(x)

print(x)
```

El programa se ejecuta sin problemas si se ingresa un valor numérico válido mayor o igual a cero; de lo  
contrario, se detiene y emite el siguiente mensaje:  
```
Traceback (most recent call last):
  File ".main.py", line 4, in 
    assert x >= 0.0
AssertionError
```  

<br></br>


## **Puntos Clave**  

1. No se puede agregar más de un bloque ```except``` sin nombre después de los bloques con nombre.  
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

2. Todas las excepciones de Python predefinidas forman una jerarquía, es decir, algunas de ellas son más generales (la llamada  
```BaseException``` es la más general)  mientras que otras son más o menos concretas (por ejemplo, ```IndexError``` es más concreta  
que ```LookupError```).  
No debes poner excepciones más concretas antes de las más generales dentro de la misma secuencia de bloques ```except```. Por  
ejemplo, puedes hacer esto:
```
try:
    # Código arriesgado.
except IndexError:
    # Solucionando problemas con listas.
except LookupError:
    # Lidiando con búsquedas erróneas.
```  
Pero no hagas esto (a menos que estés absolutamente seguro de que quieres que alguna parte de tu código sea inaccesible).  
```
try:
    # Código arriesgado.
except LookupError:
    # Lidiando con búsquedas erróneas.
except IndexError:
    # Nunca llegarás aquí. 
```  
<br></br>

3. La sentencia de Python ```raise ExceptionName``` puede generar una excepción bajo demanda. La misma sentencia pero sin  
*ExceptionName*, se puede usar **solamente** dentro del bloque ```try```, y genera la misma excepción que se está manejando  
actualmente.  
<br></br>

4. La sentencia de Python ```assert expression``` evalúa la *expresión* y genera la excepción ```AssertError``` cuando la *expresión* es  
igual a cero, una cadena vacía o ```None```. Puedes usarla para proteger algunas partes críticas de tu código de datos devastadores.  

<br></br>  


#  
[Ejercicios](Sec7-ej.md)
<br></br>

[Soluciones](Sec7-ejsol.md)  

#

[Volver a: Módulo 2 - Cadenas, métodos de listas y excepciones](../README.md)