# **Ejercicio de Laboratorio: Triángulo**

## **Tiempo Estimado**  

30-60 minutos  


## **Nivel de dificultad**  

Fácil/medio  


## **Objetivos**  

- Mejorar las habilidades del estudiante para definir clases desde cero.
- Emplear composición.


## **Escenario**  
Ahora vamos a colocar la clase ```Point``` (ver [Sección 4 Laboratorio 3](Sec4-Lab3.md)) dentro de otra clase. Además, vamos a poner tres  
puntos en una clase, lo que nos permitirá definir un triángulo. Cómo podemos hacerlo?  

La nueva clase se llamará ```Triangle``` y esto es lo que queremos:  
- El constructor acepta tres argumentos - todos ellos son objetos de la clase ```Point```.  
- Los puntos se almacenan dentro del objeto como una lista privada.  
- La clase proporciona un método sin parámetros llamado ```perimeter()```, que calcula el perímetro del  
triángulo descrito por los tres puntos; el perímetro es la suma de todas las longitudes de los lados (lo  
mencionamos para que conste, aunque estamos seguros de que tú mismo lo conoces perfectamente).  

Completa la plantilla que te proporcionamos en el editor, ejecuta tu código y verifica si tu salida se ve igual que  
la nuestra.  
```
import math


class Point:
    #
    # El código copiado del laboratorio anterior.
    #


class Triangle:
    def __init__(self, vertice1, vertice2, vertice3):
        #
        # Escribir el código aquí.
        #

    def perimeter(self):
        #
        # Escribir el código aquí.
        #


triangle = Triangle(Point(0, 0), Point(1, 0), Point(0, 1))
print(triangle.perimeter())
```

A continuación puedes copiar el código de la clase ```Point```, el cual se utilizó en el laboratorio anterior:  
```
class Point:
    def __init__(self, x=0.0, y=0.0):
        self.__x = x
        self.__y = y
```  

<br></br>  


## **Salida esperada**  
```
3.414213562373095
```  


<br></br>

#  

[Volver a: Seccion 4 - PPO: Métodos](_Seccion4.md)   

# 

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)