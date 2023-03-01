# ***PPO: Propiedades***  
<br></br>  

## **Variables de instancia**  
En general, una clase puede equiparse con dos tipos diferentes de datos para formar las propiedades de una clase. Ya viste uno de  
ellos cuando estábamos estudiando pilas.  

Este tipo de propiedad existe solo cuando se crea explícitamente y se agrega a un objeto. Como ya sabes, esto se puede hacer  
durante la inicialización del objeto, realizada por el constructor.  

Además, se puede hacer en cualquier momento de la vida del objeto. Es importante mencionar también que cualquier propiedad  
existente se puede eliminar en cualquier momento.  

Tal enfoque tiene algunas consecuencias importantes:  
- Diferentes objetos de la misma clase **pueden poseer diferentes conjuntos de propiedades**.
- Debe haber una manera de **verificar con seguridad si un objeto específico posee la propiedad** que deseas utilizar (a menos  
que quieras generar una excepción, siempre vale la pena considerarlo).  
- Cada objeto **lleva su propio conjunto de propiedades**, no interfieren entre sí de ninguna manera.  

Tales variables (propiedades) se llaman **variables de instancia**.  

La palabra *instancia* sugiere que están estrechamente conectadas a los objetos (que son instancias de clase), no a las clases mismas.  
Echemos un vistazo más de cerca.  

Aquí hay un ejemplo:
```
class ExampleClass:
    def __init__(self, val = 1):
        self.first = val

    def set_second(self, val):
        self.second = val


example_object_1 = ExampleClass()
example_object_2 = ExampleClass(2)

example_object_2.set_second(3)

example_object_3 = ExampleClass(4)
example_object_3.third = 5

print(example_object_1.__dict__)
print(example_object_2.__dict__)
print(example_object_3.__dict__)
```  
Se necesita una explicación adicional antes de entrar más en detalles. Echa un vistazo a las últimas tres líneas del código.  

Los objetos de Python, cuando se crean, están dotados de un **pequeño conjunto de propiedades y métodos predefinidos**. Cada  
objeto los tiene, los quieras o no. Uno de ellos es una variable llamada ```__dict__``` (es un diccionario).  

La variable contiene los nombres y valores de todas las propiedades (variables) que el objeto contiene actualmente. Vamos a usarla  
para presentar de forma segura el contenido de un objeto.  

Vamos a sumergirnos en el código ahora:  
<br></br>
- La clase llamda ```ExampleClass``` tiene un constructor, el cual **crea incondicionalmente una variable de instancia** llamada  
```first```, y le asigna el valor pasado a través del primer argumento (desde la perspectiva del usuario de la clase) o el segundo  
argumento (desde la perspectiva del constructor); ten en cuenta el valor predeterminado del parámetro: cualquier cosa que  
puedas hacer con un parámetro de función regular también se puede aplicar a los métodos.  
<br></br>
- La clase también tiene un **método que crea otra variable de instancia**, llamda ```second```.   
<br></br> 
- Hemos creado tres objetos de la clase ```ExampleClass```, pero todas estas instancias difieren:  
<br></br>
    - ```Example_object_1``` solo tiene una propiedad llamada ```first```.
    - ```Example_object_2``` tiene dos propiedades:```first``` y ```second```.
    - ```Example_object_3``` ha sido enrriquecido sobre la marcha con una propiedad llamada ```third``` fuera del código de la clase:  
Esto es posible y totalmente permisible.  
<br></br>

La salida del programa muestra claramente que nuestras suposiciones son correctas: aquí están:  
```
{'first': 1}
{'second': 3, 'first': 2}
{'third': 5, 'first': 4}
```  
Hay una conclusión adicional que debería mencionarse aquí: **el modificar una variable de instancia de cualquier objeto no tiene**  
**impacto en todos los objetos restantes**. Las variables de instancia estan perfectamente aisladas unas de otras.  
<br></br>  


## **Variables de instancia: continuación**  
Observa el ejemplo modificado en el editor.  
```
class ExampleClass:
    def __init__(self, val = 1):
        self.__first = val

    def set_second(self, val = 2):
        self.__second = val


example_object_1 = ExampleClass()
example_object_2 = ExampleClass(2)

example_object_2.set_second(3)

example_object_3 = ExampleClass(4)
example_object_3.__third = 5


print(example_object_1.__dict__)
print(example_object_2.__dict__)
print(example_object_3.__dict__)
```
Es casi lo mismo que el anterior. La única diferencia está en los nombres de las propiedades. Hemos  
**antepuesto dos guiones bajos (```__```)**.  

Como sabes, tal adición hace que la variable de instancia sea **privada**, se vuelve inaccesible desde el mundo  
exterior.  

El comportamiento real de estos nombres es un poco más complicado, así que ejecutemos el programa. Esta es  
la salida:  
```
{'_ExampleClass__first': 1}
{'_ExampleClass__first': 2, '_ExampleClass__second': 3}
{'_ExampleClass__first': 4, '__third': 5}
```  
Puedes ver estos nombres extraños llenos de guiones bajos? de dónde provienen?  

Cuando Python ve que deseas agregar una variable de instancia a un objeto y lo vas a hacer dentro de  
cualquiera de los métodos del objeto, **maneja la operación** de la siguiente manera:  
- Coloca un nombre de clase antes de tu nombre.  
- Coloca un guión bajo adicional al principio.  

Es por ello que ```__first``` se convierte en ```_ExampleClass__first```.  

**El nombre ahora es completamente accesible desde fuera de la clase**. Puedes ejecutar un código como  
este:  
```
print(example_object_1._ExampleClass__first)
```  



<br></br>
#  
[Ejercicios](/Modulo3/Seccion3/Sec3-ej.md)
<br></br>
[Soluciones](/Modulo3/Seccion3/Sec3-ejsol.md)  

#

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)