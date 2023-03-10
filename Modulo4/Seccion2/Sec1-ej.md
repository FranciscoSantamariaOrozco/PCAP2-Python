# **EJERCICIOS SECCION 4**  
<br></br>  

## **Ejercicio 1**  

Cuál es el resultado esperado del siguiente código?  
```python
class Vowels:
    def __init__(self):
        self.vow = "aeiouy "  # Sí, sabemos que y no siempre se considera una vocal.
        self.pos = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.pos == len(self.vow):
            raise StopIteration
        self.pos += 1
        return self.vow[self.pos - 1]


vowels = Vowels()
for v in vowels:
    print(v, end=' ')
```

<br></br>  

## **Ejercicio 2**  

Escribe una función **lambda**, estableciendo a 1 su argumento entero, y aplícalo a la función *map()* para producir la cadena ```1 3 3```  
```5``` en la consola.  
```python
any_list = [1, 2, 3, 4]
even_list = # Completar las líneas aquí.
print(even_list)
```

<br></br>  

## **Ejercicio 3**  

Cuál es el resultado esperado del siguiente código?  
```python
def replace_spaces(replacement='*'):
    def new_replacement(text):
        return text.replace(' ', replacement)
    return new_replacement


stars = replace_spaces()
print(stars("And Now for Something Completely Different"))
```

<br></br>  

#  
<br></br>

- [Soluciones](Sec1-ejsol.md)
<br></br>
#  

[Volver a: Seccion 1 - Generadores y cierres](_Seccion1.md)  

[Volver a: Módulo 4 - Misceláneo](../README.md)