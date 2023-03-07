# **EJERCICIOS SECCION 5**  
<br></br>  

## **Escenario**  
El siguiente fragmento de código se ha ejecutado con éxito:  
```
class Dog:
    kennel = 0
    def __init__(self, breed):
        self.breed = breed
        Dog.kennel += 1
    def __str__(self):
        return self.breed + " dice: ¡Guau!"


class SheepDog(Dog):
    def __str__(self):
        return super().__str__() + " ¡No huyas, corderito!"


class GuardDog(Dog):
    def __str__(self):
        return super().__str__() + " ¡Quédese donde está, intruso!"


rocky = SheepDog("Collie")
luna = GuardDog("Dobermann")
```  
Ahora responde las preguntas de los ejercicios 1-4.  

## **Ejercicio 1**  
Cuál es el resultado esperado del siguiente código?
```
print(rocky)
print(luna)
```

<br></br>  

## **Ejercicio 2**  
Cuál es el resultado esperado del siguiente código?
```
print(issubclass(SheepDog, Dog), issubclass(SheepDog, GuardDog))
print(isinstance(rocky, GuardDog), isinstance(luna, GuardDog))
```

<br></br> 

## **Ejercicio 3**  
Cuál es el resultado esperado del siguiente código?
```
print(luna is luna, rocky is luna)
print(rocky.kennel)
```

<br></br>  

## **Ejercicio 4**  
Define una subclase de ```SheepDog``` llamada ```LowlandDog```, y equipala con un método ```__str__()``` que anule un método heredado del  
mismo nombre. El nuevo método ```__str__()``` debe retornar la cadena "¡Guau! ¡No me gustan las montañas!".

<br></br>  
#  
<br></br>

- [Soluciones](Sec5-ejsol.md)
<br></br>
#  

[Volver a: Seccion 5 - Fundamentos de PPO: Herencia](_Seccion5.md)  

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)