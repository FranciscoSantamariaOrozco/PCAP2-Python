# **EJERCICIOS SECCION 4**  
<br></br>  

## **Ejercicio 1**  

La declaración de la clase ```Snake``` se muestra a continuación. Enriquece la clase con un método llamado ```increment()```, el cual  
incrementa en ```1``` la propiedad ```victims```.  
```
class Snake:
    def __init__(self):
        self.victims = 0
```

<br></br>  

## **Ejercicio 2**  

Redefine el constructor de la clase ```Snake``` para que tenga un parámetro que inicialice el campo ```victims``` con un valor pasado al  
objeto durante la construcción.

<br></br>  

## **Ejercicio 3**  

Puedes predecir el resultado del siguiente código?  
```
class Snake:
    pass


class Python(Snake):
    pass


print(Python.__name__, 'es una', Snake.__name__)
print(Python.__bases__[0].__name__, 'puede ser una', Python.__name__)
```

<br></br>  

#  
<br></br>

- [Soluciones](Sec4-ejsol.md)
<br></br>
#  

[Volver a: Seccion 4 - PPO: Métodos](_Seccion4.md)  

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)