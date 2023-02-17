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
