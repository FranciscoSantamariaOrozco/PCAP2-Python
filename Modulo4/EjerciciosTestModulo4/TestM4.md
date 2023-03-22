# **Test Modulo 4**  

1. Cuál es el resultado esperado del siguiente código?  
```python
def my_fun():
    for num in range(3):
        yield num

for i in my_fun():
    print(i)
```  
- SyntaxError
- 
```
0
1
2
```
- ```generator object my_fun at algún número hexadecimal```

<br></br>

2. Cuál es el resultado esperado del siguiente código?  
```python
foo = [i + i for i in range(5)]
print(foo)
```
- ```[1, 3, 5, 7, 9]```
- 
```
0
2
4
6
8
```
- ```0, 2, 4, 6, 8```

<br></br>

3. Cuál es el resultado esperado del siguiente código?  
```python
x = lambda a, b: a**b
print(x(2, 10))
```
- ```SyntaxError```
- ```2222222222```
- ```1024```
<br></br>

4. Selecciona las sentencias **verdaderas** con respecto a la función ```map()```. (Selecciona **dos** respuestas)
    - El primer argumento de la función ```map()``` puede ser una lista.
    - La función ```map()``` puede aceptar **más** de dos argumentos.
    - El segundo argumento de la función ```map()``` puede ser una lista.
    - La función ```map()``` puede aceptar **solamente** dos argumentos.
<br></br>

5. Selecciona las sentencias **verdaderas** respecto a la función ```filter()```. (Selecciona **dos** respuestas)
    - La función ```filter()``` tiene la siguiente sintaxis: ```filter(iterable, function)```.
    - La función ```filter()``` devuelve un iterador.
    - La función ```filter()``` **no** devuelve un iterador.
    - La función ```filter()``` tiene la siguiente sintaxis: ```filter(function, iterable)```.
<br></br>

6. Cuál es el resultado esperado del siguiente código?
```python
numbers = (1, 2, 5, 9, 15)

def filter_numbers(num)
    nums = (1, 5, 17)
    if num in nums:
        return True
    else:
        return False

filtered_numbers = filter(filter_numbers, numbers)
for n in filtered_numbers
    print(n)
```
 - ```2, 9, 15```
 - ```SyntaxError```
 - 
```
1
5
```
<br></br>

7. Cuáles de las siguientes sentencias son **verdaderas**? (Selecciona **dos** respuestas)
    - La función ```map()``` crea una copia de su segundo argumento y le aplica el primer argumento.
    - Una lista por compresión se convierte en un generador cuando se utiliza entre paréntesis (por ejemplo, ```()```), no con corchetes  
(por ejemplo, ```[]```).
    - La sentencia ```yield``` debe ser empleada fuera de las funciones.
    - La declaración de una función ```lambda``` es la misma que la de una función regular.
<br></br>

8. Los dos modos básicos de apertura de archivos, mutuamente excluyentes, se denominan:
    - De texto e imagen.
    - Binario y de texto.
    - Binario y ternario.
<br></br>

9. Un método capaz de leer datos de un archivo y pasarlos a un arreglo de bytes se denomina:
    - ```readinto()```
    - ```readout()```
    - ```readin()```
<br></br>

10. Qué sucede si se ejecuta el siguiente código, asumiendo que el directorio ```d``` ya existe?
```python
import os
os.mkdir("/a/b/c/d")
```

- Python sobreescribirá el directorio existente.
- Se genera una excepción ```DirectoryExistError```
- Se genera una excepción ```FileExistError```

<br></br>  

11. Qué sucede si se ejecuta el siguiente código?  
```python
import time

time.sleep(30)
print("!Despierta!")
```  
- La cadena ```!Despierta!``` se mostrará en la pantalla después de 30 segundos.
- La cadena ```!Despierta!``` se mostrará treinta veces en la pantalla durante 30 segundos.
- La cadena ```!Despierta!``` se mostrará en la pantalla durante 30 segundos.  

<br></br> 

12. Cuál es el resultado esperado del siguiente código?  
```
import calendar

cal = calendar.isleap(2019)
print(cal)
```  
- ```True```
- ```False```
- ```None```

<br></br>

#
- [Soluciones](soltest_mod4.md)
#  
[Volver a: Módulo 4 - Miscelánea](../README.md)