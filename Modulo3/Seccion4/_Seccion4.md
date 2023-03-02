# ***PPO: Métodos***  
<br></br>  

## **Métodos a detalle**  
Resumamos todos los hechos relacionados con el uso de métodos en las clases de Python.  

Como ya sabes, un **método es una función que está dentro de una clase**.  

Existe un requisito fundamental: un **método esta obligado a tener al menos un parámetro** (no existen  
métodos sin parámetros; un método puede invocarse sin un argumento, pero no puede declararse sin  
parámetros).  

El primer (o único) parámetro generalmente se denomina ```self```. Te sugerimos que lo sigas nombrando  
de esta manera, darle otros nombres puede causar sorpresas inesperadas.  

El nombre *self* sugiere el propósito del parámetro: **identifica el objeto para el cual se invoca el método**.  

Si vas a invocar un método, no debes pasar el argumento para el parámetro ```self```, Python lo configurará por  
ti.  

El ejemplo en el editor muestra la diferencia.  
```
class Classy:
    def method(self):
        print("método")


obj = Classy()
obj.method()
```  

El código da como salida:  
```
método
```  

Toma en cuenta la forma en que hemos creado el objeto, hemos **tratado el nombre de la clase como una**  
**función**, y devuelve un objeto recién instanciado de la clase.  
#  
Si deseas que el método acepte parámetros distintos a ```self```, debes:  
- colocarlos después de ```self``` en la definición del método.  
- Pasarlos como argumentos durante la invocación sin especificar ```self```.  

Justo como aquí:  
```
class Classy:
    def method(self, par):
        print("método:", par)


obj = Classy()
obj.method(1)
obj.method(2)
obj.method(3)
```  

El código da como salida:  
```
método: 1
método: 2
método: 3
```  

<br></br>  


## **Métodos al detalle: continuación**  
El parámetro ```self``` es usado **para obtener acceso a la instancia del objeto y las variables de clase**.  

El ejemplo muestra ambas formas de utilizar el parámetro ```self```:  
```
class Classy:
    varia = 2
    def method(self):
        print(self.varia, self.var)


obj = Classy()
obj.var = 3
obj.method()
```  

El código da como salida:  
```
2 3
```  

El parámetro ```self``` también se usa **para invocar otros métodos desde dentro de la clase**.  

Justo como aquí:  
```
class Classy:
    def other(self):
        print("otro")

    def method(self):
        print("método")
        self.other()


obj = Classy()
obj.method()
```  

El código da como salida:  
```
método
otro
```

<br></br>
#  
[Ejercicios](/Modulo3/Seccion3/Sec3-ej.md)
<br></br>
[Soluciones](/Modulo3/Seccion3/Sec3-ejsol.md)  

#

[Volver a: Módulo 3 - Programación Orientada a Objetos y Procesamiento de Archivos en Python](../README.md)