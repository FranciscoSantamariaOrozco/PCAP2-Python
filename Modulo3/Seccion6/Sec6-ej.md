# **EJERCICIOS SECCION 6**  
<br></br>   

## **Ejercicio 1**  
Cuál es el resultado esperado del siguiente código?
```
import math

try:
    print(math.sqrt(9))
except ValueError:
    print("inf")
else:
    print("ok")
```

<br></br>  

## **Ejercicio 2**  
Cuál es el resultado esperado del siguiente código?
```
import math

try:
    print(math.sqrt(-9))
except ValueError:
    print("inf")
else:
    print("ok")
finally:
    print("fin")
```

<br></br> 

## **Ejercicio 3**  
Cuál es el resultado esperado del siguiente código?
```
import math

class NewValueError(ValueError):
    def __init__(self, name, color, state):
        self.data = (name, color, state)

try:
    raise NewValueError("Advertencia enemiga", "Alerta roja", "Alta disponibilidad")
except NewValueError as nve:
    for arg in nve.args:
        print(arg, end='! ')
```

<br></br>  

#  
<br></br>

- [Soluciones](Sec6-ejsol.md)
<br></br>
#  

[Volver a: Seccion 6 - Excepciones una vez más](_Seccion6.md)  

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)