# **Ejercicio de Laboratorio: Los módulos datetime y time**

## **Tiempo Estimado**  

30-60 minutos  


## **Nivel de dificultad**  

Fácil  


## **Objetivos**  

- Mejorar las habilidades del estudiante en el uso de la clase *Calendar*.  

## **Escenario**  
Durante este curso, echamos un breve vistazo a la clase ```Calendar```. Tu tarea ahora es ampliar su  
funcionalidad con un nuevo método llamado ```count_weekday_in_year```, que toma un año y un día de la  
semana como parámetros, y luego devuelve el número de ocurrencias de un día de la semana específico en el  
año.  

Utiliza los siguientes consejos:  
- Crea una clase llamada ```MyCalendar``` que se extiende de la clase ```Calendar```.  
- Crea el método ```count_weekday_in_year``` con los parámetros de year y weekday. El parámetro  
weekday debe tener un valor entre 0 y 6, donde 0 es el Lunes y 6 es el Domingo. El método debe devolver  
el número de días como un número entero.  
- En tu implementación, usa el método ```monthdays2calendar``` de la clase ```Calendar```.  
<br></br>

Los siguientes son resultados esperados de ejemplo:  

**Argumentos de muestra**
```
year=2019, weekday=0
```

**Salida esperada**  
```
52
```
<br></br>

**Argumentos de muestra**
```
year=2000, weekday=6
```

**Salida esperada**  
```
53
```

<br></br>

#  

[Volver a: Seccion 6 - El módulo *calendar*](_Seccion5.md)  

# 

[Volver a: Módulo 4 - Misceláneo](../README.md)