# **Examen Modulo 3**  

1. El comando ```pip list``` presenta una lista de:
    - Todos los paquetes disponibles en PyPI
    - Comandos pip disponibles
    - Paquetes locales obsoletos
    - Paquetes instalados localmente
<br></br>  
<br></br>

2. Sabiendo que una función llamada ```fun``` reside dentro de un módulo llamado ```mod```, y se ha importado usando la siguiente linea:  
```
import mod
```
Selecciona la fiorma en que se puede invocar desde tu código.   
importarlo.  

   - ```import fun```
   - ```from fun import mod```
   - ```import fun from mod```
   - ```from mod import fun```
<br></br>  
<br></br>

3. Durante la primera importación de un módulo, Python despliega los archivos *pyc* en el directorio llamado:  

   - ```hasbang```
   - ```mymodules```
   - ```__pycache__```
   - ```__init__```
<br></br>  
<br></br>

4. Sabiendo que una función llamda ```fun()``` reside dentro de un módulo llamado ```mod```, selecciona la forma correcta de  
importarlo.  

    - ```import fun```
    - ```from fun import mod```
    - ```import fun from mod```
    - ```from mod import fun```
<br></br>  
<br></br>

5. Selecciona las sentencias **verdaderas**. (selecciona **dos** respuestas).  

    - La función ```system``` del módulo ```platform``` devuelve una cadena con el nombre de tu sistema operativo.
    - La función ```processor``` del módulo ```platform``` devuelve un número entero con la cantidad de procesos que se están ejecutando  
actualmente en tu sistema operativo.
   - La función ```version``` del módulo ```platform``` devuelve una cadena con la versión de tu instalación de Python.
   - La función ```version``` del módulo ```platform``` devuelve una cadena con la versión de tu sistema operativo..
<br></br>    
<br></br>

6. La sigiente línea de código:  
```from a.b import c```  
causa la importación de:  
   - la entidad ```b``` del módulo ```a``` del paquete ```c```
   - la entidad ```c``` del módulo ```b``` del paquete ```a```
   - la entidad ```c``` del módulo ```a``` del paquete ```b```
   - la entidad ```a``` del módulo ```b``` del paquete ```c```
<br></br>  
<br></br>

7. Una variable predefinida de Python que almacena el nombre del módulo actual lleva por nombre:  
    - ```__name__```
    - ```__modname__```
    - ```__mod__```
    - ```__module__```
<br></br>  
<br></br>

8. Cuál es el resultado esperado del siguiente código?  
```
from random import randint  

for i in range(2):  
    print(randint(1, 2), end='')
```
   - ```11```,```12```,```21```, o ```22```
   - Existen millones de combinaciones posibles y no se puede predecir el resultado exacto.
   - ```12```
   - ```12```, o ```21```
<br></br>  
<br></br>

9. Cuáles de las siguientes sentencias son **verdaderas** acerca del comando ```pip install```? (Selecciona **dos** respuestas) 

    - Permite al usuario instalar una versión específica del paquete.
    - Instala un paquete por usuario cuando la opcion ```user``` es especificada.
    - Instala un paquete en todo el sistema cuando la opcion ```--system``` es especificada.
    - Siempre instala la versión más reciente del paquete y eso no se puede cambiar.
<br></br>  
<br></br>

10.   Una función que devuelve una lista de todas las entidades disponibles en un módulo lleva por nombre:  
- ```listmodule()```
- ```entities()```
- ```dir()```
- ```content()```
<br></br>  
<br></br>

11.    Cuál es el valor esperado asignado a la variable ```result``` después de que se ejecute el siguiente código?  
```
import math  

result = math.e != math.pow(2, 4)  
print(int(result))
```  

- ```1```
- ```False```
- ```0```
- ```True```
<br></br>  
<br></br>

12.  Cuando se importa un módulo, su contenido: 
     - Se ejecuta una vez (implícitamente).
     - Es ignorado.
     - Puede ser ejecutado (explícitamente).
     - Se ejecuta tantas veces como se importe.
<br></br>  
<br></br>

13.   Un archivo *pyc* contiene:  
      - Código compilado de Python
      - Código fuente de Python
      - Un intérprete de Python
      - Un compilador de Python
<br></br>  
<br></br>

14.   Se puede obtener una lista de las dependencias de los paquetes en ```pip``` empleando el comando:  
      - ```deps```
      - ```show```
      - ```dir```
      - ```list```
<br></br>  
<br></br>

15.   Qué comando de ```pip``` se puede emplear para eliminar un paquete instalado?  
      - ```pip uninstall package```
      - ```pip remove package```
      - ```pip --uninstall package```
      - ```pip install --uninstall package```
<br></br>  
<br></br>

16. Cuál de las siguientes sentencias es **verdadera** acerca de la actualización de paquetes de Python ya instalados?  
      - Es realizada por el comando ```install``` acomoañado de la opción ```U```.
      - Se puede hacer reinstalando el paquete usando el comando ```reinstall```
      - Es un proceso automático que no requiere la atención del usuario.
      - Solo se puede hacer desinstalando e instalando los paquetes una vez más.
<br></br>  
<br></br>

17. El conjunto de caracteres escrito como ```#!``` se emplea para:  
    
    - Hacer que una entidad de módulo en particular sea privada.
    - Decirle a un sistema operativo MS Windows cómo ejecutar el contenido de un archivo Python.
    - Decirle a un sistema operativo Unix o similar a Unix cómo ejecutar el contenido de un archivo Python.
    - Crear un docstring (cadena de documentación)
<br></br>  
<br></br>

18.  Cuáles de las siguientes sentencias son **verdaderas** acerca del comando ```pipsearch```? (selecciona **dos** respuestas).  

- Busca en todos los paquetes de PyPI
- Necesita una conexión a internet para funcionar.
- Todas sus búsquedas están limitadas a paquetes instalados localmente.
- Busca solo a través de los nombres de los paquetes.

<br></br>  
<br></br>  

#
- [Soluciones](soltest_mod3.md)
#  
[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)