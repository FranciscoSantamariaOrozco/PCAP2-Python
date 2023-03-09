# **EJERCICIOS SECCION 3**  

<br></br>


## **Ejercicio 1**  

Cuál es el resultado esperado del siguiente código?
```
for ch in "abc123XYX":
    if ch.isupper():
        print(ch.lower(), end='')
    elif ch.islower():
        print(ch.upper(), end='')
    else:
        print(ch, end='')
```  

<br></br>



## **Ejercicio 2**  

Cuál es el resultado esperado del siguiente código?
```
s1 = '¿Dónde están las nevadas de antaño?'
s2 = s1.split()
print(s2[-2])
```

<br></br>


## **Ejercicio 3**  

Cuál es el resultado esperado del siguiente código?
```
the_list = ['¿Dónde', 'están', 'las', 'nevadas?']
s = '*'.join(the_list)
print(s)
```

<br></br>


## **Ejercicio 4**  

Cuál es el resultado esperado del siguiente código?
```
s = 'Es fácil o imposible'
s = s.replace('fácil', 'difícil').replace('im', '')
print(s)
```


#  
<br></br>

- [Soluciones](Sec3-ejsol.md)
<br></br>  

#  

[Volver a: Seccion 3 - Métodos de cadenas](_Seccion3.md)  

[Volver a: Módulo 2 - Cadenas, métodos de listas y excepciones](../README.md)