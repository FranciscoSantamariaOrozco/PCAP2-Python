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
La clase ```date``` nos da la capacidad de crear un objeto del tipo *fecha* a partir de una *marca de tiempo*.  

En Unix, la marca de tiempo expresa el número de segundos desde el 1 de Enero de 1970 a las 00:00:00 (UTC).  
Esta fecha se llama la **época Unix**, por que es cuando comenzó el conteo del tiempo en los sistemas Unix.  

La marca de tiempo es en realidad la diferencia entre una fecha en particular (incluida la hora) y el 1 de enero de  
1970, 00:00:00 (UTC), expresada en segundos.

Para crear un objeto de fecha a partir a partir de una marca de tiempo, debemos pasar una marca de tiempo Unix al  
método ```fromtimestamp```.  

Para este propósito, podemos usar el módulo ```time```, que proporciona funciones relacionadas con el tiempo.  
Uno de ellos es una función llamada ```time()```, que devuelve el número de segundos desde el 1 de enero de  
1970 hasta el momento actual en forma de número flotante. Echa un vistazo al ejemplo en el editor.  
```python
from datetime import date
import time

timestamp = time.time()
print("Marca de tiempo:", timestamp)

d = date.fromtimestamp(timestamp)
print("Fecha:", d)
```  

Ejecuta el código para ver el resultado.  

Si ejecutas el código de muestra varias veces, podrás ver cómo se incrementa la marca de tiempo. Vale la pena  
agregar que el resultado de la función ```time``` depende de la plataforma, porque **en los sistemas Unix y**  
**Windows, los segundos intercalares no se cuentan**.  

**Nota**: En esta parte del curso también hablaremos sobre el módulo *time*.  

<br></br>  


## **Creando un objeto de fecha usando el formato ISO**.  
El módulo ```datetime``` proporciona varios métodos para crear un objeto ```date```. Uno de ellos es el método  
```fromisoformat```, que toma una fecha en el formato **AAAA-MM-DD** compatible con el estándar ISO 8601.  

El estándar ISO 8601 define cómo se representan la fecha y la hora. Se usa a menudo, por lo que vale la pena  
tomarse un momento para familiarizarse con él. Echa un vistazo a la imagen que describe los valores requeridos  
por el formato:  

<p align="center">
<img src="img/fechahoraiso.jpg">
</p>  

Ahora observa el código en el editor y ejecútalo.  
```python
from datetime import date

d = date.fromisoformat('2019-11-04')
print(d)
```
En nuestro ejemplo, AAAA es 2019, MM es 11 (noviembre) y DD es 04 (cuarto de noviembre).  

Cuando sustituyas la fecha, asegúrate de agregar 0 antes de un mes o de un día expresado por un número  
menor que 10.  

**Nota**: El método ```fromisoformat``` ha estado disponible en Python desde la versión 3.7.  

<br></br>  


## **El método *replace()***  
A veces, es posible que debas reemplazar el año, el mes o el día con un valor diferente. No puedes hacer esto  
con los atributos de año, mes y día por que son de solo lectura. En este caso, puedes utilizar el método llamado  
```replace```.  

Ejecuta el código en el editor:  
```python
from datetime import date

d = date(1991, 2, 5)
print(d)

d = d.replace(year=1992, month=1, day=16)
print(d)
```  

Resultado:  
```
1991-02-05
1992-01-16
```  

Los parámetros *year*, *month* y *day* son opcionales. Puedes pasar solo un parámetro al método ```replace```, por  
ejemplo, *año*, o los tres como en el ejemplo.  

El método ```replace``` devuelve un objeto ```date``` modificado, por lo que debes recordar asignarlo a alguna variable.  

<br></br>  


## **Que día de la semana es?**  
Uno