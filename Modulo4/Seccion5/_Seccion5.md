#  
[Ejercicios](/Modulo4/Seccion5/Sec5-ej.md)
<br></br>

[Soluciones](/Modulo4/Seccion5/Sec5-ejsol.md)  

#

[Volver a: Módulo 4 - Miscelaneo](../README.md)
# **El módulo *datetime***  

<br></br>  

## **Introducción al módulo *datetime***  
En esta sección, aprenderás sobre un módulo de Python llamado *datetime*.  

Como puedes adivinar, proporciona **clases para trabajar con la fecha y hora**. Si crees que no necesitas profundizar en este tema,  
hablemos de ejemplos del uso de la fecha y la hora en la programación.  

La fecha y la hora tienen innumerables usos y probablemente sea difícil encontrar una aplicación de producción que no os utilice.  
A continuación, se muestran algunos ejemplos:  

- **Registro de eventos**: gracias al conocimiento de la fecha y la hora, podemos determinar cuándo ocurre exactamente un error  
crítico en nuestra aplicación. Al crear registros, puedes especificar el formato de fecha y hora.  

- **Seguimiento de cambios en la base de datos**: a veces es necesario almacenar información sobre cuándo se creó o modificó un  
registro. El módulo *datetime* será perfecto para eso.  

- **Validación de datos**: pronto aprenderás a leer la fecha y hora actuales en Python. Conociendo la fecha y hora actuales, podrás  
validar varios tipos de datos, por ejemplo, si un cupón descuento ingresado por un usuario en nuestra aplicación sigue siendo  
válido.  

- **Almacenamiento de información importante**: te imaginas transferencias bancarias sin almacenar la finromación de  
cuándo se realizaron? La fecha y la hora de ciertas acciones deben conservarse y debemos ocuparnos de ello.  

<p align="center">
<img src="img/logodatetime.jpg">
</p>  

La fecha y la hora se utilizan en casi todas las áreas de nuestras vidas, por lo que es importante familiarizarse con el módulo *datetime*  
de Python. Estás listo para una nueva dosis de conocimiento?  

<br></br>  


## **Obtener la fecha local actual y crear objetos del tipo fecha**  
Una de las clases proporcionadas por el módulo ```datetime``` es una clase llamada ```date```. Los objetos de esta  
clase representan una fecha que consta de año, mes y día. Mira el código en el editor para ver cómo se ve en la  
práctica y como obtener la fecha local actual usando el método ```today```.  
```python
from datetime import date

today = date.today()

print("Hoy:", today)
print("Año:", today.year)
print("Mes:", today.month)
print("Día:", today.day)
```  

Ejecuta el código para ver qué sucede.  

El método ```today``` devulve un objeto del tipo ```date``` que representa la fecha local actual. Toma en cuenta que  
el objeto ```date``` tiene tres atributos: *año*, *mes* y *día*.  

Ten cuidado, porque estos atributos son de solo lectura. Para crear un objeto ```date```, debes pasar los  
parámetros *año*, *mes* y *día* de la siguiente manera:  
```python
from datetime import date

my_date = date(2019, 11, 4)
print(my_date)
```  

Ejecuta el ejemplo para ver qué sucede.  
<br></br>

Al crear un objeto *date* toma en cuenta las siguientes restricciones:  

<table>
    <tr>
        <td height='50pt'><b>Parámetro</b></td>
        <td height='50pt', width='700pt'><b>Restricciones</b></td>
    </tr>
    <tr>
        <td><code>año</code></td>
        <td height='50pt', width='700pt'>El parámetro <i>año</i> debe ser mayor o igual a 1 (constante MINYEAR) y menor o igual a 9999 (constante MAXYEAR).</td>
    </tr>
    <tr>
        <td><code>mes</code></td>
        <td height='50pt', width='700pt'>El parámetro <i>mes</i> debe ser mayor o igual a 1 y menor o igual a 12.</td>
    </tr>
    <tr>
        <td><code>día</code></td>
        <td height='50pt', width='700pt'>El parámetro <i>día</i> debe ser mayor o igual a 1 y menor o igual que el último día del mes y año indicados.</td>
    </tr>
</table>  
<br></br>

**Nota**: más adelante en este curso, aprenderás a cambiar el formato de fecha predeterminado.  

<br></br>  


## **Creación de un objeto de fecha a partir de una marca de tiempo**  
La clase ```date``` nos