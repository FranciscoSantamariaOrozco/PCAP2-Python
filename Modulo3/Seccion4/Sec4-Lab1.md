# **Ejercicio de Laboratorio: La clase Timer**

## **Tiempo Estimado**  

30-60 minutos  


## **Nivel de dificultad**  

Fácil/medio  


## **Objetivos**  

- Mejorar las habilidades del estudiante para definir clases desde cero.
- Definir y usar variables de instancia.  
- Definir y usar métodos.  


## **Escenario**  
Necesitamos una clase capaz de contar segundos. Fácil? No es tan fácil como podrías pensar, ya que  
tendremos algunos requisitos específicos.  

Léelos con atención, ya que la clase sobre la que escribes se utilizará para lanzar cohetes en misiones  
internacionales a Marte. Es una gran responsabilidad. Contamos contigo!  

Tu clase se llamará ```Timer``` (temporizador en español). Su constructor acepta tres argumentos que  
representan **horas** (un valor del rango [0..23]; usaremos tiempo militar), **minutos** (del rango [0..59]) y  
**segundos** (del rango [0..59]).  

Cero es el valor predeterminado para todos los parámetros anteriores. No es necesario realizar ninguna  
comprobación de validación.  

La clase en sí debería proporcionar las siguientes facilidades:  
- Los objetos de la clase deben ser "imprimibles", es decir, deben poder convertirse implícitamente en  
cadenas de la siguiente forma: "hh:mm:ss", con ceros a la izquirda agregados cuando cualquiera de los  
valores es menor que 10.  
- La clase en debe estar equipada con métodos sin parámetros llamados ```next_second()``` y  
```previous_second()```, incrementando el tiempo almacenado dentro de los objetos en +1/-1 segundos  
respectivamente.  

Emplea las siguientes sugerencias:  

- Todas las propiedades del objeto deben ser privadas.  
- Considera escribir una función separada (no un método!) para formatear la cadena con el tiempo.  

Completa la plantilla que te proporcionamos en el editor. Ejecuta tu código y comprueba si el resultado es el  
mismo que el nuestro.  
```
class Timer:
    def __init__( ??? ):
        #
        # Escribir código aquí.
        #

    def __str__(self):
        #
        # Escribir código aquí.
        #

    def next_second(self):
        #
        # Escribir código aquí.
        #

    def prev_second(self):
        #
        # Escribir código aquí.
        #


timer = Timer(23, 59, 59)
print(timer)
timer.next_second()
print(timer)
timer.prev_second()
print(timer)
```


## **Salida esperada**  
```
23:59:59
00:00:00
23:59:59
```


<br></br>

#  

[Volver a: Seccion 4 - PPO: Métodos](_Seccion4.md)   

# 

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)