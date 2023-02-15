# **Ejercicio de Laboratorio: Tu pripio Split**
```
def mysplit(strng):
    #
    # coloca tu código aquí
    #


print(mysplit("Ser o no ser, esa es la pregunta"))
print(mysplit("Ser o no ser,esa es la pregunta"))
print(mysplit("   "))
print(mysplit(" abc "))
print(mysplit(""))
```

## **Tiempo Estimado**  
  
20-25 minutos  
  

## **Nivel de dificultad**  
  
medio  
  

## **Objetivos**  
  
- Mejorar las habilidades del alumno al trabajar con cadenas.
- Utilizar losmétodos incorporados de Python para las cadenas.  
  

## **Escenario**  
  
Ya sabes como funciona el método ```split()```. Ahora queremos que lo pruebes.  
  
Tu tarea es **escribir tu pripia función, que se comporte casi como el método original** ```split()```, por  
ejemplo:  
  
- Debe aceptar únicamente un argumento: una cadena.
- Debe devolver una lista de palabras creadas a partir de la cadena, dividida en los lugares donde la cadena  
contiene espacios en blanco.  
- Si la cadena está vacía, la función debería devolver una lista vacía.  
- Su nombre debe ser ```mysplit()```  

Utiliza la plantilla en el editor. Prueba tu código con cuidado.  
  
  
## **Salida esperada**  
```
['Ser', 'o', 'no', 'ser', 'esa', 'es,', 'la', 'pregunta']
['Ser', 'o', 'no', 'ser,esa', 'es', 'la', 'pregunta']
[]
['abc']
[]
```