# **Ejercicio de Laboratorio: Colas alias FIFO**

## **Tiempo Estimado**  

20-45 minutos  


## **Nivel de dificultad**  

Fácil/medio  


## **Objetivos**  

- Mejorar las habilidades del estudiante para definir clases desde cero.
- Implementar estructuras de datos estándar como clases.


## **Escenario**  

Como ya sabes, una *pila* es una estructura de datos que realiza el modelo LIFO (último en entrar, primero en  
salir). Es fácil y ya te has acostumbrado a ello perfectamente.  

Probemos algo nuevo ahora. Una *cola (queue)* es un modelo de datos caracterizado por el término **FIFO:**  
**primero en entrar, primero en salir**. Nota: una cola (fila) regular que conozcas de las tiendas u oficinas de  
correos funciona exactamente de la misma manera: un cliente que llegó primero también es el primero en ser  
atendido.  

Tu tarea es implementar la clase ```Queue``` con dos operaciones básicas:  
- ```put(elemento)```, que coloca un elemento al final de la cola.  
- ```get()```, que toma un elemento del principio de la cola y lo devuelve como resultado (la cola no puede  
estar vacía para realizarlo correctamente).  

Sigue las sugerencias:  
- Emplea una lista como tu almacenamiento (como lo hicimos con la pila).  
- ```put()``` debe agregar elementos al principio de la lista, mientras que ```get()``` debe de eliiminar los  
elementos del final de la lista.  
- Define una nueva excepción llamada ```QueueError``` (elige una excepción de la cual se derivará) y generala  
cuando ```get()``` intente operar en una lista vacía.  

Completa el código que te proporcionamos en el editor. Ejecútalo para comprobar si tu salida es similar a la  
nuestra.  
```
class QueueError(???):  # Eligir la clase base para la nueva excepción.
    #
    #  Escribe código aquí.
    #


class Queue:
    def __init__(self):
        #
        # Escribe código aquí.
        #

    def put(self, elem):
        #
        # Escribe código aquí.
        #

    def get(self):
        #
        # Escribe código aquí.
        #


que = Queue()
que.put(1)
que.put("perro")
que.put(False)
try:
    for i in range(4):
        print(que.get())
except:
    print("Error de Cola")
```

## **Salida Esperada**  
```
1
perro
False
Error de Cola
```  


<br></br>

#  

[Volver a: Seccion 2 - Un corto viaje desde el enfoque procedimental hacia el orientado a objetos.](_Seccion2.md)   

# 

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)