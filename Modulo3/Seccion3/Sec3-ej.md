# **EJERCICIOS SECCION 3**  
<br></br>  

## **Ejercicio 1**  

Cuáles de las propiedades de la clase ```Python``` son variables de instancia y cuáles son variables de clase? Cuáles de ellos son  
privados?  
```
class Python:
    population = 1
    victims = 0
    def __init__(self):
        self.length_ft = 3
        self.__venomous = False
```

<br></br>  

## **Ejercicio 2**  

Vas a negar la propiedad ```__venomous``` del objeto ```version_2```, ignorando el hecho de que la propiedad es privada. Cómo vas a  
hacer esto?  
```
version_2 = Python()
```

<br></br>  

## **Ejercicio 3**  

Escribe una expresión que compruebe si el objeto ```version_2``` contiene una propiedad de instancia denominada ```constrictor```  
(sí, constrictor!).

<br></br>  

#  
<br></br>

- [Soluciones](Sec3-ejsol.md)
<br></br>
#  

[Volver a: Seccion 3 - ](_Seccion3.md)  

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)