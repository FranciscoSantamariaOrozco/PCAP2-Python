
<br></br>

#  
[Ejercicios](/Modulo4/Seccion1/Sec1-ej.md)
<br></br>

[Soluciones](/Modulo3/Seccion1/Sec1-ejsol.md)  

#

[Volver a: Módulo 4 - Miscelaneo](../README.md)
# **Generadores y cierres**  

<br></br>  

## **Generadores, donde encontrarlos**  
**Generador** - Con qué asocias esta palabra? Quizás se refiere a un dispositivo electronico. O tal vez se refiere  
a una máquina pesada diseñada para producir energía eléctrica u otra cosa.  

Un generador de Python es **un fragmento de código especializado capaz de producir una serie de valores y**  
**controlar el proceso de iteración**. Esta es la razón por la cual los generadores a menudo se llaman **iteradores**,  
y aunque hay quienes pueden encontrar una diferencia entre estos dos, aquí los trataremos como uno mismo.  

Puede que no te hayas dado cuenta, pero te has topado con generadores muchas, muchas veces antes. Echa un  
vistazo al fragmento de código:  
```python
for i in range(5):
    print(i)
```  
La función ```range()``` es un generador, la cual también es un iterador.  

Cuál es la diferencia?  

Una función devuelve un valor bien definido, el cual, puede ser el resultado de una evaluación compleja, por  
ejemplo, de un polinomio, y se invoca una vez, solo una vez.  

Un generador **devuelve una serie de valores**, y en general, se invoca (implícitamente) más de una vez.  

En el ejemplo, el generador ```range()```  se invoca seis veces, proporcionando cinco valores de cero a cuatro.  

El proceso anterior es completamente transparente. Vamos a arrojar algo de luz sobre el. Vamos a mostrarte el  
**protocolo iterador**.  

<br></br>  


## **Generadores, donde encontrarlos: continuación**  
El **protocolo iterador es una forma en que un objeto debe comportarse para ajustarse a las reglas**  
**impuestas por el contexto de las sentencias** ```for``` **e** ```in```. Un objeto conforme al protocolo iterador se llama  
**iterador**.  

Un iterador debe proporcionar dos métodos:  
- ```__iter__()``` el cual debe **devolver el objeto en sí** y que se invoca una vez (es necesario para que  
Python inicie con éxito la iteración).  
- ```__next__()``` el cual debe **devolver el siguiente valor** (primero, segundo, etc.) de la serie deseada: será  
invocado por las sentencias ```for```/```in``` para pasar a la siguiente iteración; si no hay más valores a  
proporcionar, el método deberá **generar la excepción** ```StopIteration```.  

Suena extraño? De ninguna manera. Mira el ejemplo en el editor.  
```python
1 | class Fib:
2 |   def __init__(self, nn):
3 |       print("__init__")
4 |       self.__n = nn
5 |       self.__i = 0
6 |       self.__p1 = self.__p2 = 1
7 |
8 |   def __iter__(self):
9 |       print("__iter__")
10|        return self
11|
12|    def __next__(self):
13|        print("__next__")		
14|        self.__i += 1
15|        if self.__i > self.__n:
16|            raise StopIteration
17|        if self.__i in [1, 2]:
18|            return 1
19|        ret = self.__p1 + self.__p2
20|        self.__p1, self.__p2 = self.__p2, ret
21|        return ret
22|
23|
24| for i in Fib(10):
25|    print(i)
```  

Hemos creado una clase capaz de iterar a través de los primeros ```n``` valores (donde ```n``` es un parámetro del  
constructor) de los números de Fibonacci.  

Permítenos recordarte: los números de Fibonacci(*Fib*), se definen de la siguiente manera:  

Fib<sub>1</sub> = 1  
Fib<sub>2</sub> = 1  
Fib<sub>3</sub> = Fib<sub>1</sub> + 1Fib<sub>2</sub>  

En otras palabras:  
- Los primeros dos números de Fibonacci son 1.  
- Cualquier otro número de Fibonacci es la suma de los dos anteriores (por ejemplo, Fib<sub>3</sub>=2, Fib<sub>4</sub>=3, Fib<sub>5</sub>=5,  
y así sucesivamente)  

Vamos a ver el código:  
- Las líneas 2 a 6: El constructor de la clase imprime un mensaje (lo usaremos para rastrear el  
comportamiento de la clase), se preparan algunas variables:(```__n``` para almacenar el límite de la serie,  
```__i``` para rastrear el número actual de la serie Fibonacci, y ```__p1``` junto con ```__p2``` para guardar los dos  
números anteriores).  

- Las líneas 8 a 10: el método ```__iter__``` está obligado a devolver el objeto iterador en sí mismo; su  
propósito puede ser un poco ambiguo aquí, 