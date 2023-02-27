# **SOLUCIONES EJERCICIOS SECCION 2**  
<br></br>  

## **Ejercicio 1**  

Suponiendo que hay una clase llamada ```Snakes```, escribe la primera línea de la declaración de clase ```Python```, expresando el hecho  
de que la nueva clase es en realidad una subclase de Snake.

```
class Python(Snakes):
```

<br></br>  

## **Ejercicio 2**  

Algo falta en la siguiente declaración, qué es?
```
class Snakes
    def __init__():
        self.sound = 'Sssssss'
```

El constructor ```__init__``` carece del parámetro obligatorio (deberíamos llamarlo ```self``` para cumplir con los estándares).
<br></br>  

## **Ejercicio 3**  

Modifica el código para garantizar que la propiedad ```venomous``` sea privada.
```
class Snakes
    def __init__(self):
        self.venomous = True
```  
El código debería verse como sigue:  
```
class Snakes
    def __init__(self):
        self.__venomous = True
```

<br></br>  

#  
<br></br>

- [Ejercicios](Sec2-ej.md)
<br></br>
#  

[Volver a: Seccion 2 - Un corto viaje desde el enfoque procedimental hacia el orientado a objetos.](_Seccion2.md)  

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)