# **EJERCICIOS SECCION 2**  
<br></br>  

## **Ejercicio 1**  

Cómo se codifica el valor del argumento modo de la función ```open()``` si se va a crear un nuevo archivo de texto?

<br></br>  

## **Ejercicio 2**  

Cuál es el significado del valor representado por ```errno.EACESS```?

<br></br>  

## **Ejercicio 3**  

Cuál es la salida esperada del siguiente código, asumiendo que el archivo llamado *file* no existe?  
```python
import errno

try:
    stream = open("file", "rb")
    print("existe")
    stream.close()
except IOError as error:
    if error.errno == errno.ENOENT:
        print("ausente")
    else:
        print("desconocido")
```


<br></br>  

#  
<br></br>

- [Soluciones](Sec2-ejsol.md)
<br></br>

#  

[Volver a: Seccion 2 - Procesando archivos](_Seccion2.md)  

[Volver a: Módulo 4 - Misceláneo](../README.md)