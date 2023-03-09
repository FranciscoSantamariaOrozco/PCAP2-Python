# **EJERCICIOS SECCION 7**  

## **Ejercicio 1**  

Cuál es el resultado esperado del siguiente código?
```
try:
    print(1/0)
except ZeroDivisionError:
    print("cero")
except ArithmeticError:
    print("arit")
except:
    print("algo")
```  

## **Ejercicio 2**  

Cuál es el resultado esperado del siguiente código?
```
try:
    print(1/0)
except ArithmeticError:
    print("arit")
except ZeroDivisionError:
    print("cero")
except:
    print("algo")
```

## **Ejercicio 3**  

Cuál es el resultado esperado del siguiente código?
```
def foo(x):
    assert x
    return 1/x


try:
    print(foo(0))
except ZeroDivisionError:
    print("cero")
except:
    print("algo")
```

#  
<br></br>

- [Soluciones](Sec7-ejsol.md)
<br></br>  

#  

[Volver a: Seccion 7 - La anatomía de las excepciones](_Seccion7.md)  

[Volver a: Módulo 2 - Cadenas, métodos de listas y excepciones](../README.md)