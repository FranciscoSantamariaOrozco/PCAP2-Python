## **Trabajando con módulos estándar**  
  
Antes de comenzar a revisar algunos módulos estándar de Python, veamos la función ```dir()```. No tiene nada que ver con el comando  
```dir()``` de las terminales de Windows o Unix. El comando ```dir()``` no muestra el contenido de un directorio o carpeta de disco, pero no  
se puede negar que hace algo similar: puede revelar todos los nombres proporcionados a través de un módulo en particular.  
  
Existe una condición: el módulo debe haberse importado previamente como un todo (es decir, utilizar la instrucción ```import```  
```module``` - ```from module``` no es suficiente).  
  
La función devuelve una **lista ordenada alfabéticamente** la cual contiene todos los nombres de las entidades disponibles en el  
módulo:  
```
dir(module)
```  
  
Nota: Si el nombre del módulo tiene un alias, debes usar el alias, no el nombre original.  
  
Usar la función dentro de un script normal no tiene mucho sentido, pero aún así, es posible.  
  
Por ejemplo, se puede ejecutar el siguiente código para imprimir los nombres de todas las entidades dentro del módulo ```math```:  
```
import math  
  
for name in dir(math):  
    print(name, end="\t")
```  
  
El código de ejemplo debería producir el siguiente resultado:  
```
__doc__ __loader__  __name__    __package__ __spec__    acos    acosh   asin  
asinh   atan    atan2   atanh   ceil    copysign    cos cosh    degrees e   erf  
erfc    exp expm1   fabs    factorial   floor   fmod    frexp   fsum    gamma   hypot  
isfinite    isinf   isnan   ldexp   lgamma  log log10   log1p   log2    modf    pi  
pow radians sin sinh    sqrt    tan tanh    trunc
```  
  
Has notado los nombres extraños que comienzan con ```__``` al inicio de la lista? Se hablará de ellos cuando hablemos sobre los  
problemas relaccionados con la escritura de módulos propios.  
  
Algunos de los nombres pueden traer recuerdos de las lecciones de matemáticas, y probablemente no tendrás ningún problema en  
adivinar su significado.  
  
El emplear la función ```dir()``` dentro de un código puede no parecer muy útil; por lo general, se desea conocer el contenido de un  
módulo en particular antes de escribir y ejecutar el código.  
  
Afortunadamente, se puede ejecutar la función **directamente en la consola de Python** (IDLE), sin necesidad de escribir y ejecutar un  
script por separado.  
  
Así es como se puede hacer:  
```
import math
dir(math)
```  
  
Deberías ver algo similar a esto:  
![dirmath](../img/dirmath.jpg)  
  
  
## **Funciones seleccionadas del módulo *math***  
  
Comencemos con una vista previa de algunas de las funciones proporcionadas por el módulo ```math```.  
  
Se han elegido algunas arbitrariamente, pero esto no significa que las funciones no mencionadas aquí sean  
menos signficativas. Tómate el tiempo para revisar las demás por ti mismo: no tenemos el espacio ni el tiempo  
para hablar de todas a detalle.  
  
El primer grupo de funciones de módulo ```math``` están relaccionadas con **trigonometría**:  
  
- ```sin(x)``` -> es el seno de x.
- ```cos(x)``` -> es el coseno de x.
- ```tan(x)``` -> es la tangente de x.  
  
Todas estas funciones toman un argumento (una medida de ángulo expresada en radianes) y devuelven el  
resultado apropiado (ten cuidado con ```tan()``` - no todos los argumentos son aceptados).  
  
Por supuesto, también están sus versiones inversas:  
  
- ```asin(x)``` -> es el arcoseno de x.
- ```acos(x)``` -> es el arcocoseno de x.
- ```atan(x)``` -> es el arcotangente de x.  
  
Estas funciones toman un argumento (verifican que sea correcto) y devuelven una medida de un ángulo en  
radianes.  
  
  
Para trabajar eficazmente con mediciones de ángulos, el módulo ```math``` proporciona las siguientes entidades:  
  
- ```pi``` -> una constante con un valor que es una aproximación de π.
- ```radians(x)``` -> una función que convierte el x de grados a radianes.
- ```degrees(x)``` -> una función que convierte x de radianes a grados.  
  
  
Ahora observa el código en el editor. El programa de ejemplo no es muy sofisticado, pero puedes predecir sus  
resultados?  
  
```
from math import pi, radians, degrees, sin, cos, tan, asin

ad = 90
ar = radians(ad)
ad = degrees(ar)

print(ad == 90.)
print(ar == pi / 2.)
print(sin(ar) / cos(ar) == tan(ar))
print(asin(sin(ar)) == ar)
```
  
Además de las funciones circulares (enumeradas anteriormente), en el módulo ```math``` también contiene un  
conjunto de sus **análogos hiberbólicos**:  
  
- ```sinh(x)``` -> el seno hiperbólico.
- ```cosh(x)``` -> el coseno hiperbólico.
- ```tanh(x)``` -> el tangente hiperbólico.
- ```asinh(x)``` -> el arcoseno hiperbólico.
- ```acosh(x)``` -> el arcocoseno hiperbólico.
- ```atanh(x)``` -> el arcotangente hiperbólico.  
  
  
## **Funciones seleccionadas del módulo *math*: continuación**  
  
Existe otro grupo de las funciones ```math``` relaccionadas con la **exponenciación**:  
  
- ```e``` -> una constante con un valor que es una aproximación del número de Euler (e).
- ```exp(x)``` -> encontrar el valor de e<sup>x</sup>.
- ```log(x)``` -> el logaritmo natural de x.
- ```log(x , b)``` -> el logaritmo de x con base b.
- ```log10(x)``` -> el logaritmo decimal de x (más preciso que ```log(x , 10)```).
- ```log2(x)``` -> el logaritmo binario de x (más preciso que ```log(x , 2)```).  
  
  
Nota: la función ```pow()```:  
  
- ```pow(x , y)``` -> encuentra el valor de x<sup>y</sup> (toma en cuenta los dominios).  
  
Esta es una función incorporada y no se tiene que importar.  
  
Observa el código el editor. Puedes predecir su salida?  
```
from math import e, exp, log

print(pow(e, 1) == exp(log(e)))
print(pow(2, 2) == exp(2 * log(2)))
print(log(e, e) == exp(0))
```  
  
