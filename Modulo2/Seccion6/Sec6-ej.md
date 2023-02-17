# **EJERCICIOS SECCION 6**  

## **Ejercicio 1**  

Cuál es el resultado esperado del siguiente código?
```
try:
    print("Tratemos de hacer esto")
    print("#"[2])
    print("¡Tuvimos éxito!")
except:
    print("Hemos fallado")
print("Hemos terminado")
```  

## **Ejercicio 2**  

Cuál es el resultado esperado del siguiente código?
```
try:
    print("alpha"[1/0])
except ZeroDivisionError:
    print("cero")
except IndexingError:
    print("índice")
except:
    print("algo")
```
