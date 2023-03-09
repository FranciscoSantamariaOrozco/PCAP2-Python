# **EJERCICIOS SECCION 6**  

<br></br>


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

<br></br>


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

#  
<br></br>

- [Soluciones](Sec6-ejsol.md)
<br></br>  


#  
[Volver a: Seccion 6 - Errores: el pan diario del programador](_seccion6.md)  

[Volver a: Módulo 2 - Cadenas, métodos de listas y excepciones](../README.md)