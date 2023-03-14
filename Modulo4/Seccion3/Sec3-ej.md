# **EJERCICIOS SECCION 3**  
<br></br>  

## **Ejercicio 1**  

Qué se espera del método ```readlines()``` cuando el stream está asociado con un archivo vacío?

<br></br>  

## **Ejercicio 2**  

Qué se pretende hacer con el siguiente código?  
```python
for line in open("file", "rt"):
    for char in line:
        if char.lower() not in "aeiouy ":
            print(char, end='')
```

<br></br>  

## **Ejercicio 3**  

Vas a procesar un mapa de bits almacenado en un archivo llamado ```image.png``` y quieres leer su  
contenido como un todo en una variable *bytearray* llamada ```image```. Agrega una línea al siguiente  
código para lograr este objetivo.  
```python
try:
    stream = open("image.png", "rb")
    # Inserta una línea aquí.
    stream.close()
except IOError:
    print("fallido")
else:
    print("exitoso")
```


<br></br>  

#  
<br></br>

- [Soluciones](Sec3-ejsol.md)
<br></br>

#  

[Volver a: Seccion 3 - Trabajando con archivos reales](_Seccion3.md)  

[Volver a: Módulo 4 - Misceláneo](../README.md)