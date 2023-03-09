## **Comparando cadenas**  
Las cadenas en Python **pueden ser comparadas usando el mismo conjunto de operadores** que se emplean  
con los números.  

Observa estos operadores: también sirven para comparar cadenas:  

- ```==```
- ```!=```
- ```>```
- ```>=```
- ```<```
- ```<=```  

Existe un "pero": los resultados de tales comparaciones a veces pueden ser un poco soprendentes. No olvides  
que Python no es consciente (no puede serlo de ninguna manera) de problemas lingüísticos sutiles.  
Simplemente **compara valores de puntos de código**, carácter por carácter.  

Los resultados que se obtienen de una operación de este tipo a veces son sorprendentes. Comencemos con los  
casos más simples.  

Dos cadenas son iguales cuando consisten de los mismos caracteres en el mismo orden. Del mismo modo, dos  
cadenas no son iguales cuando no consisten de los mismos caracteres en el mismo orden.  

Ambas comparaciones dan ```True``` (verdadero) como resultado:  
```
'alpha' == 'alpha'
'alpha' != 'Alpha'
```  

La relaión entre cadenas se determina al **comparar el primer carácter diferente en ambas cadenas** (ten en  
cuenta los puntos de código ASCII / UNICODE en todo momento).  

Cuando se comparan dos cadenas de diferentes longitudes y la más corta es idéntica a la más larga, la **cadena**  
**más larga se considera mayor**.  

Justo como aquí:  
```
'alpha' < 'alphabet'
```  

La comparación es ```True``` (verdadera).  

La comparación de cadenas siempre distingue entre mayúsculas y minúsculas (**las letras mayúsculas se**  
**consideran menores en comparación con las minúsculas**).  

La expresión es ```True``` (verdadera):  
```
'beta' > 'Beta'
```  

<br></br>


## **Comparando cadenas: continuación**  
Aún **si una cadena contiene solo dígitos, todavía no es un número**. Se interpreta como lo que es, como  
cualquier otra cadena regular, y su aspecto numérico (potencial) no se toma en cuenta, en ninguna manera.  

Observa los ejemplos:  
```
'10' == '010'
'10' > '010'
'10' > '8'
'20' < '8'
'20' < '80'
```  

Producen los siguientes resultados:  
```
False
True
False
True
True
```  

**El comparar cadenas con los números generalmente es una mala idea.**  

Las únicas comparaciones que se puede realizar con impunidad son aquellas simbolizadas por los operadores  
```==``` y ```!=```. El primero siempre devuelve ```False``` (falso), mientras que el segundo siempre devuelve ```True```  
(verdadero).  

El uso de cualquiera de los operadores de comparación restantes generará una excepción *TypeError*.  

Vamos a verlo:  
```
'10' == 10
'10' != 10
'10' == 1
'10' != 1
'10' > 10
```  

Los resultados en este caso son:  
```
False
True
False
True
TypeError exception
```  

Ejecuta todos los ejemplos y realiza más experimentos.  

<br></br>


## **Ordenamiento**  
La comparación está estrechamente relacionada con el ordenamiento (o más bien, el ordenamiento es, de  
hecho, un caso muy sofisticado de comparación).  

Esta es una buena oportunidad para mostrar dos formas posibles de **ordenar listas que contienen cadenas**.  
Dicha operación es muy común en el mundo real: cada vez que ves una lista de nombres, productos, títulos o  
ciudades, esperas que este ordenada.  

Supongamos que deseas ordenar la siguiente lista:  
```
 greek = ['omega', 'alpha', 'pi', 'gamma']

```  

En general, Python ofrece dos formas diferentes de ordenar las listas.  

El primero se implementa con una función llamada ```sorted()```.  

La función toma un argumento (una lista) y **retorna una nueva lista**, con los elementos ordenados del  
argumento. (Nota: esta descripción está un poco simplificada en comparación con la implementación real; lo  
discutiremos más adelante).  

La lista original permanece intacta.  

Observa el código en el editor y ejecútalo.  
```
# Demostración de la función sorted():
first_greek = ['omega', 'alpha', 'pi', 'gamma']
first_greek_2 = sorted(first_greek)

print(first_greek)
print(first_greek_2)

print()

# Demostración del método sort():
second_greek = ['omega', 'alpha', 'pi', 'gamma']
print(second_greek)

second_greek.sort()
print(second_greek)
```  

El código produce el siguiente resultado:  
```
['omega', 'alpha', 'pi', 'gamma']
['alpha', 'gamma', 'omega', 'pi']
```  

El segundo método afecta a la lista misma - **no se crea una nueva lista**. El ordenamiento se realiza por el  
método denominado ```sort()```.  
<br></br>

La salida no ha cambiado:  
```
['omega', 'alpha', 'pi', 'gamma']
['alpha', 'gamma', 'omega', 'pi']
```  

Si necesitas un ordenamiento diferente, debes convencer a la función o método de cambiar su comportamiento  
predeterminado. Lo discutiremos pronto.  

<br></br>


## **Cadenas frente a números**  
Hay dos cuestiones adicionales que deberían discutirse aquí: **Cómo convertir un número (un entero o un**  
**flotante) en una cadena, y viceversa?** Puede ser necesario realizar tal transformación. Además, es una forma  
rutinaria de procesar datos de entrada o salida.  

La conversión de cadena a número es simple, ya que siempre es posible. Se realiza mediante una función  
llamada ```str()```.  

Justo como aquí:
```
itg = 13
flt = 1.3
si = str(itg)
sf = str(flt)

print(si + ' ' + sf)
```  

La salida del código es:
```
13 1.3
```  
<br></br>
La transformación inversa solo es posible cuando la cadena representa u  número válido. Si no se cumple la  
condición, espera una excepción **ValueError**.  

Emplea la función ```int()``` si deseas obtener un entero, y ```float()``` si necesitas un valor punto flotante.  

Justo como aquí:  
```
si = '13'
sf = '1.3'
itg = int(si)
flt = float(sf)

print(itg + flt)
```  

Esto es lo que verás en la consola:  
```
14.3
```  

En la siguiente sección, te mostraremos algunos programas simples que procesan cadenas.  

<br></br>


## **Puntos Claves**  
1. Las cadenas se pueden comparar con otras cadenas utilizando operadores de comparación generales, pero compararlas con  
números no da un resultado razonable, por que **ninguna cadena puede ser igual** a ningún otro número. Por ejemplo:  

- ```cadena == número``` es siempre ```False``` (falso)
- ```cadena != número``` es siempre ```True``` (verdadero)
- ```cadena >= número``` siempre **genera una excepción**.  

<br></br>

2. El ordenamiento de listas de cadenas se puede realizar mediante:  

- Una función llamada ```sorted()```, crea una nueva, lista ordenada.
- Un método llamado ```sort()```, el cual ordena la lista *en el momento*.  

<br></br>  

3. Un número se puede convertir en una cadena empleando la función ```str()```  

<br></br>  

4. Una cadena se puede convertir en un número (aunque no todas las cadenas) empleando ya sea la función ```int()``` o ```float()```. La  
conversión falla si la cadena no contiene un número válido (se genera una excepción en dicho caso).  

<br></br>  


#  
[Ejercicios](Sec4-ej.md)
<br></br>

[Soluciones](Sec4-ejsol.md)  
<br></br>

[Laboratorio](Sec4-Lab1.md)

#

[Volver a: Módulo 2 - Cadenas, métodos de listas y excepciones](../README.md)