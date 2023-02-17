# **Ejercicio de Laboratorio: Un display LED**

## **Tiempo Estimado**  
  
30 minutos  
  

## **Nivel de dificultad**  
  
medio  
  

## **Objetivos**  
  
- Mejorar las habilidades del alumno al trabajar con cadenas.
- Usar cadenas para representar datos que no son texto. 
  

## **Escenario**  
  
Seguramente has visto un *display de siete segmentos*.  
  
Es un dispositivo (a veces electrónico, a veces mecánico) diseñado para presentar un dígito decimal utilizando  
un subconjunto de siete segmentos. Si aún no sabes lo qué es, consulta el siguiente enlace en Wikipedia:
[https://en.wikipedia.org/wiki/Seven-segment_display](https://en.wikipedia.org/wiki/Seven-segment_display)  
  
Tu tarea es escribir **un programa que puede simular el funcionamiento de un display de siete segmentos**.  
aunque vas a usar LEDs individuales en lugar de segmentos.  
  
Cada dígito es construido con 13 LEDs (algunos iluminados, otros apagados, por supuesto), así es como lo  
imaginamos:  
```
  # ### ### # # ### ### ### ### ### ### 
  #   #   # # # #   #     # # # # # # # 
  # ### ### ### ### ###   # ### ### # # 
  # #     #   #   # # #   # # #   # # # 
  # ### ###   # ### ###   # ### ### ###
```  
  
Nota: el número 8 muestra todas las luces led encendidas.  
  
Tu código debe *mostrar* cualquier número entero no negativo ingresado por el usuario.  
  
Consejo: puede ser muy útil usar una lista que contenga patrones de los diez dígitos.  
  

## **Datos de prueba**  
  
Entrada de muestra:
```
123
```  
  
Salida de muestra:
```
 # ### ### 
  #   #   # 
  # ### ### 
  # #     # 
  # ### ### 
```  
  
Entrada de muestra:  
```
9081726354
```  
  
Salida de muestra:  
```
### ### ###   # ### ### ### ### ### # # 
# # # # # #   #   #   # #     # #   # # 
### # # ###   #   # ### ### ### ### ### 
  # # # # #   #   # #   # #   #   #   # 
### ### ###   #   # ### ### ### ###   # 
```