# **SOLUCIONES EJERCICIOS SECCION 2**  
<br></br>  

## **Ejercicio 1**  

Qué se espera del método ```readlines()``` cuando el stream está asociado con un archivo vacío?  

Se espera una lista vacía (una lista de longitud cero).

<br></br>  

## **Ejercicio 2**  

Qué se pretende hacer con el siguiente código?  
```python
for line in open("file", "rt"):
    for char in line:
        if char.lower() not in "aeiouy ":
            print(char, end='')
```  

Copia el contenido del archivo *file* hacia la consola, ignorando las vocales.

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

```python
image = bytearray(stream.read())
```

<br></br>  

#  
<br></br>

- [Ejercicios](Sec3-ej.md)
<br></br>

#  

[Volver a: Seccion 3 - Trabajando con archivos reales](_Seccion3.md)  

[Volver a: Módulo 4 - Misceláneo](../README.md)