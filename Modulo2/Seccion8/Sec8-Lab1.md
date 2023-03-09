# **Ejercicio de Laboratorio: Leer enteros de forma segura**  
```
def read_int(prompt, min, max):
    #
    # Escribe tu código aquí.
    #


v = read_int("Ingresa un numero entre -10 a 10: ", -10, 10)

print("El número es:", v)

```

## **Tiempo Estimado**  

15-25 minutos  


## **Nivel de dificultad**  

medio  


## **Objetivos**  

- Mejorar las habilidades del alumno al definir funciones.
- Utilizar excepciones para proporcionar un entorno de entrada más seguro.  


## **Escenario**  
Tu tarea es escribir una **función capaz de ingresar valores enteros y verificar si están dentro de un rango**  
**Especificado**.  

La función deberá:  
- Aceptar tres argumentos: una entrada, un límite inferior aceptable y un límite superior aceptable.  
- Si el usuario ingresa una cadena que no es un valor entero, la función debe emitir el mensaje ```Error:```  
```entrada incorrecta```, y solicitará al usuario que ingrese el valor nuevamente.  
- Si el usuario ingresa un número que está fuera del rango especificado, la función debe emitir el mensaje  
```Error: el valor no está dentro del rango permitirdo (min..max)``` y solicitará al usuario que  
ingrese el valor nuevamente.  
- Si el valor de entrada es válido, será regresado como resultado.


## **Datos de Prueba**  
Prueba tu código cuidadosamente.  

Así es como la función debería reaccionar ante la entrada del usuario:  
```
Ingresa un número entre -10 a 10: 100
Error: el valor no está dentro del rango permitido (-10..10)
Ingresa un número entre -10 a 10: asd
Error: entrada incorrecta
Ingresa un número entre -10 a 10: 1
El número es: 1
```  

<br></br>  

#  

[Volver a: Seccion 8 - Excepciones útiles](_Seccion8.md)  

[Volver a: Módulo 2 - Cadenas, métodos de listas y excepciones](../README.md)