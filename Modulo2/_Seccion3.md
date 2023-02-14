## **El método *capitalize()***  
  
Veamos algunos métodos estándar de cadenas en Python. Vamos a analizarlos en orden alfabético, cualquier  
orden tiene tanto desventajas como ventajas, por lo que la elección puede ser aleatoria.  
  
El método ```capitalize()``` hace exactamente lo que dice - **crea una nueva cadena con los caracteres**  
**tomados de la cadena fuente**, pero intenta modificarlos de la siguiente manera:  
  
- **Si el primer carácter dentro de la cadena es una letra** (nota: el primer carácter es el elemento con un  
índice igual a *0*, no es el primer carácter visible), **se convertirá a mayúsculas**.  
- **Todas las letras restantes de la cadena se convertirán a minúsculas**.  
  
No olvides que:  
- La cadena original desde la cual se invoca el método no se cambia de ninguna manera, la inmutabilidad de  
una cadena debe obedecerse sin reservas.  
- La cadena modificada (en mayúscula en este caso) se devuelve como resultado; si no se usa de alguna  
manera (asígnala a una variable o pásala a una función / método) desaparecerá sin dejar rastro.  
  
Nota: Los métodos no tienen que invocarse solo dentro de las variables. Se pueden invocar directamente desde  
dentro de literales de cadena. Usaremos esa convención regularmente: simplificará los ejemplos, ya que los  
aspectos más importantes no desapareerán entre asignaciones innecesarias.  
  
Echa un vistazo al ejemplo en el editor. Ejecútalo.
```
# Demostración del método capitalize():
print('aBcD'.capitalize())
```  
  
Esto es lo que imprime:
```
Abcd
```  
  
Prueba algunos ejemplos más avanzados y verifica su salida:
```
print("Alpha".capitalize())
print('ALPHA'.capitalize())
print(' Alpha'.capitalize())
print('123'.capitalize())
print("αβγδ".capitalize())
```  
  
  
## **El método *center()***  
  
La variante de un parámetro del método ```center()``` **genera una copia de la cadena original, tratando de**  
**centrarla dentro de un campo de un ancho especificado**.  
  

El centrado se realiza realmente al **agregar algunos espacios antes y después de la cadena**.  
  
No esperes que este método demuestre habilidades sofisticadas. Es bastante simple.  
  
El ejemplo en el editor usa corchetes para mostrar claramente donde comienza y termina realmente la cadena  
centrada.  
```
# Demostración del método center():
print('[' + 'alpha'.center(10) + ']')
```
  
Su salida se ve de la siguiente manera:  
```
[  alpha   ]
```  
  
Si la longitud del campo de destino es demasiado pequeña para ajustarse a la cadena, se devuelve la cadena  
original.  
  
Puedes ver el método ```center()``` en más ejemplos aquí:  
```
print('[' + 'Beta'.center(2) + ']')
print('[' + 'Beta'.center(4) + ']')
print('[' + 'Beta'.center(6) + ']')
```  
  
Ejecuta el código anterior y verifica que salidas produce.  
  
**La variante de dos parámetros de ```center``` hace usodel carácter del segundo argumento, en lugar de**  
**un espacio**. Analiza el siguiente ejemplo:  
```
print('[' + 'gamma'.center(20, '*') + ']')
```  
  
Es por eso que la salida ahora se ve así.  
```
[*******gamma********]
```  
  
Realiza más experimentos.  
  

## **El método *endswitch()***  
  
El método ```endswitch()``` **comprueba si la cadena dada termina con el argumento especificado y devuelve**  
```True (Verdadero)``` **o** ```False (Falso)```, dependiendo del resultado.  
  
Nota: la subcadena debe adherirse al último carácter de la cadena; no se puede ubicar en algún lugar cerca del  
final de la cadena.  
  
Observa el ejemplo en el editor, analízalo y ejecútalo.
```
# Demostración del método endswith():
if "epsilon".endswith("on"):
    print("si")
else:
    print("no")
```  
  
Su salida es:  
```
si
```  
  
Ahora deberías poder predecir la salida del fragmento de código a continuación:
```
t = "zeta"
print(t.endswith("a"))
print(t.endswith("A"))
print(t.endswith("et"))
print(t.endswith("eta"))
```  
  
Ejecuta el código para verificar tus predicciones.  
  

## **El método *find()***  
  
El método ```find()``` es similar al método ```index()``` el cual ya conoces - **busca una subcadena y devuelve el**  
**índice de la primera aparición de esta subcadena**, pero:  
  
- **Es más seguro, no genera un error para un argumento que contiene una subcadena inexistente**  
(devuelve ```-1``` en dicho caso).  
- Funciona **solo con cadenas** - no intentes aplicarlo a ninguna otra secuencia.  

Analiza el código en el editor. Así es como puedes usarlo.  
```
# Demostración del método find():
print("Eta".find("ta"))
print("Eta".find("mma"))
```  
  
El ejemplo imprime:  
```
1
-1
```  
  
Nota: no se debe de emplear ```find()``` si deseas verificar si un solo carácter aparece dentro de una cadena - el  
operador ```in``` será significativamente más rápido.  
  
Aquí hay otro ejemplo:  
```
t = 'theta'
print(t.find('eta'))
print(t.find('et'))
print(t.find('the'))
print(t.find('ha'))
```  
  
Puedes predecir la salida? Ejecuta el código y verifica tus predicciones.  
  
Si deseas realizar la búsqueda, no desde el principio de la cadena, sino **desde cualquier posición**, puedes usar  
una **variante de dos parámetros** del método ```find()```. Mira el ejemplo.  
```
print('kappa'.find('a', 2))
```  
  
El segundo argumento **especifica el índice en el que se iniciará la búsqueda** (no tiene que estar dentro de la  
cadena).  
  
De las dos letras *a*, solo se encontrará la segunda. Ejecuta el código y verifica.  
  

Se puede emplear el método ```find()``` para buscar todas las ocurrencias de la subcadena, como aquí:  
```
the_text = """A variation of the ordinary lorem ipsum
text has been used in typesetting since the 1960s 
or earlier, when it was popularized by advertisements 
for Letraset transfer sheets. It was introduced to 
the Information Age in the mid-1980s by the Aldus Corporation, 
which employed it in graphics and word-processing templates
for its desktop publishing program PageMaker (from Wikipedia)"""

fnd = the_text.find('the')
while fnd != -1:
    print(fnd)
    fnd = the_text.find('the', fnd + 1)
```  
  
El código imprime los índices de todas las ocurrencias del artículo *the*, y su salida se ve así:  
```
15
80
198
221
238
```  
  
Existe también una **mutación de tres parámetros del método** ```find()``` - el tercer argumento **apunta al**  
**primer índice que no se tendrá en cuenta durante la búsqueda** (en realidad es el límite superior de la  
búsqueda).  
  
Observa el ejemplo a continuación:  
```
print('kappa'.find('a', 1, 4))
print('kappa'.find('a', 2, 4))
```  
  
El segundo argumento especifica el índice en el que se iniciará la búsqueda (no tiene que estar dentro de la  
cadena).  
  
Por lo tanto, las salidas de ejemplo son:
```
1
-1
```  
  
*a* no se puede encontrar dentro de los límites de búsqueda dados en el segundo ```print()```.  
  

## **El método *isalnum()***  
  
El método sin parámetros llamado ```isalnum()``` **comprueba si la cadena contiene solo dígitos o caracteres**  
**alfabéticos (letras) y devuelve** ```True (verdadero)``` **o** ```False (falso)``` de acuerdo al resultado.  
  
Observe el ejemplo en el editor y ejecútalo.  
  
Nota: cualquier elemento de cadena que no sea un dígito o una letra hace que el método regrese  
```False (falso)```. Una cadena vacía también lo hace.  
```
# Demostración del método the isalnum():
print('lambda30'.isalnum())
print('lambda'.isalnum())
print('30'.isalnum())
print('@'.isalnum())
print('lambda_30'.isalnum())
print(''.isalnum())
```  
  
El resultado de ejemplo es:
```
True
True
True
False
False
False
```  
  
Existen tres ejemplos más aquí:  
```
t = 'Six lambdas'
print(t.isalnum())

t = 'ΑβΓδ'
print(t.isalnum())

t = '20E1'
print(t.isalnum())
```  
  
Ejecútalos y verifica su salida.  
  
Nota: la causa del primer resultado es un espeacio, no es ni un digito ni una letra.  
  

## **El método *isalpha()***  
  
El método ```isalpha()``` es más especializado, se interesa en **letras solamente**.  
```
# Ejemplo 1: Demostración del método isapha():
print("Moooo".isalpha())
print('Mu40'.isalpha())
```
  
Observa el Ejemplo 1, su salida es:  
```
True
False
```  
  
  
## **El método *isdigit()***  
  
Al contrario, el método ```isdigit()``` busca **solo dígitos** - cualquier otra cosa produce ```False (falso)``` como  
resultado.  
```
# Ejemplo 2: Demostración del método isdigit():
print('2018'.isdigit())
print("Year2019".isdigit())
```
  
Oberva el Ejemplo 2, su salida es:  
```
True
False
```  
  
Realiza más experimentos.  
  

## **El método *islower()***  
  
El método ```islower()``` es una variante de ```isalpha()``` - solo acepta **letras minúsculas**.  
```
# Ejemplo 1: Demostración del método islower():
print("Moooo".islower())
print('moooo'.islower())
```  
  
Observa el Ejemplo 1 en el editor, genera:
```
False
True
```  
  
  
## **El método *isspace()***  
  
El método ```isspace()``` **identifica espacios en blanco solamente** - no tiene en cuenta ningún otro carácter (el  
resultado es entonces ```False```).  
```
# Ejemplo 2: Demostración del método isspace(:
print(' \n '.isspace())
print(" ".isspace())
print("mooo mooo mooo".isspace())
```  
  
Observa el Ejemplo 2 en el editor, genera:
```
True
True
False
```  
  
  
## **El método *isupper()***  
  
El método ```isupper()``` es la versión en mayúscula de ```islower()``` - se concentra **solo en letras mayúsculas**.  
  
De nuevo, observa el Ejemplo 3 en el editor, genera:  
```
False
False
True
```  
  
  
## **El método *join()***  
  
El método ```join()``` es algo complicado, así que déjanos guiarte paso a paso:  
  
- Como su nombre lo indica, el método **realiza una unión** y espera un argumento del tipo lista; se debe  
asegurar que todos los elementos de la lista sean cadenas: de lo contrario, el método generará una  
exce+ción *TypeError*.  
- Todos los elementos de la lista serán **unidos en una sola cadena** pero... 
- ... la cadena desde la que se ha invocado el método será **utilizada como separador**, puesta entre las  
cadenas.  
- La cadena recién creada se devuelve como resultado.  
  

Echa un vistazo al ejemplo en el editor.
```
# Demonstrating the join() method:
print(",".join(["omicron", "pi", "rho"]))
```  
  
Vamos a analizarlo:  
  
- El método ```join()``` se invoca desde una cadena que contiene una coma (la cadena puede ser larga o  
estar vacía).  
- El argumento del ```join``` es una lista que contiene tres cadenas.  
- El método devuelve una nueva cadena.  
  
Aquí está:  
```
omicron,pi,rho
```  
  

## **El método *lower()***  
  
El método ```lower()``` **genera una copia de una cadena, reemplaza todas las letras mayúsculas con sus**  
**equivalentes en minúsculas**, y devuelve la cadena como resultado. Nuevamente, la cadena original permanece  
intacta.  
  
Si la cadena no contiene caracteres en mayúscula, el método devuelve la cadena original.  
  
Nota: El método ```lower()``` no toma ningún parámetro.  
```
# Demostración del método lower():
print("SiGmA=60".lower())
```  
  
La salida del ejemplo del editor es:  
```
sigma=60
```  
  
Como ya sabes, realiza tus propios experimentos.  
  
  
## **El método *lstrip()***  
  
El método