# **Ejercicio de Laboratorio: El módulo os**

## **Tiempo Estimado**  

15-30 minutos  


## **Nivel de dificultad**  

Fácil  


## **Objetivos**  

- Mejorar las habilidades del estudiante para interactuar con el sistema operativo.
- Uso práctico de funciones conocidas proporcionadas por el módulo *os*.


## **Escenario**  
No hjace falta decir que los sistemas operativos te permiten buscar archivos y directorios. Mientras estudiabas  
esta parte del curso, se aprendió sobre las funciones del módulo *os*, que tiene todo lo que se necesita para  
escribir un programa que buscará directorios en una ubicación determinada.  

Para facilitar tu tarea, hemos preparado una estructura de directorio de prueba para ti:  

<p align="center">
<img src="img/estructuradirectorios.jpg">
</p>  

Tu programa debe cumplir con los siguientes requisitos:  

1. Escribe una función o método llamado *find* que tome dos argumentos llamados *path* y *dir*. El argumento  
*path* debe aceptar una ruta relativa o absoluta a un directorio donde debe comenzar la búsqueda, mientras  
que el argumento *dir* debe ser el nombre de un directorio en el que deseas encontrar la ruta dada. Tu  
programa debería mostrar las rutas absolutas si encuentra un directorio con el nombre dado.  

2. La búsqueda en el directorio debe realizarse de forma recursiva. Esto significa que la búsqueda también  
debe incluir todos los subdirectorios en la ruta dada.  

**Entrada de ejemplo:**  
```
path="./tree", dir="python"
```  

**Salida de ejemplo:**  
```
.../tree/python
.../tree/cpp/other_courses/python
.../tree/c/other_courses/python
```

<br></br>

#  

[Volver a: Seccion 3 - Trabajando con archivos reales](_Seccion3.md)   

# 

[Volver a: Módulo 4 - Misceláneo](../README.md)