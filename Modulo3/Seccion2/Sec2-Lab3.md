# **Cola alias FIFO: parte 2**

## **Tiempo Estimado**  

15-30 minutos  


## **Nivel de dificultad**  

Fácil/medio  


## **Objetivos**  

- Mejorar las habilidades del estudiante para definir subclases.
- Agregar nueva funcionalidad a una clase existente.


## **Escenario**  

Tu tarea es extender ligeramente las capacidades de la clase ```Queue```.  Queremos que tenga u  método sin  
parámetros que devuelva *True* si la cola está vacía y *False* de lo contrario.  

Completa el código que te proporcionamos en el editor. Ejecútalo para comprobar si genera un resultado  
similar al nuestro.  
```
class QueueError(???):
    pass


class Queue:
    #
    # Código del laboratorio anterior.
    #


class SuperQueue(Queue):
    #
    # Escribe código nuevo aquí.
    #


que = SuperQueue()
que.put(1)
que.put("perro")
que.put(False)
for i in range(4):
    if not que.isempty():
        print(que.get())
    else:
        print("Cola vacía")
```  

A continuación, puedes copiar el código que usamos en el laboratorio anterior:  
```
class QueueError(IndexError):
    pass


class Queue:
    def __init__(self):
        self.queue = []
    def put(self,elem):
        self.queue.insert(0,elem)
    def get(self):
        if len(self.queue) > 0:
            elem = self.queue[-1]
            del self.queue[-1]
            return elem
        else:
            raise QueueError
```  

## **Salida Esperada**  
```
1
perro
False
Cola vacía
```


<br></br>

#  

[Volver a: Seccion 2 - Un corto viaje desde el enfoque procedimental hacia el orientado a objetos.](_Seccion2.md)   

# 

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)