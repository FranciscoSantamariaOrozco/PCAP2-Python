## **Qué es un paquete?**  
  
Escribir tus propios módulos no difiere mucho de escribir scripts comunes.  
  
Existen algunos aspectos específicos que se deben tomar en cuenta, pero definitivamente no es algo complicado. Lo verás pronto.  
  
![conj_paq_mod_fun](../img/conj_paq_mod_fun.jpg)  
  
Resumamos algunos aspectos importantes:  
  
- Un **módulo es un contenedor lleno de funciones** - Puedes empaquetar tantas funciones como desees en un módulo y  
distribuirlo por todo el mundo.  
- Por supuesto, no es buena idea mezclar funciones con diferentes áreas de aplicación dentro de un módulo (al igual que en  
una biblioteca: nadie espera que los trabajos científicos se incluyan entre los cómics), así que se deben agrupar las funciones  
cuidadosamente y asignar un nombre claro e intuitivo al módulo que las contiene (por ejemplo, no le des el nombre  
```videojuegos``` a un módulo que contiene funciones destinadas a particionar y formatear discos duros).  
- Crear muchos módulos puede causar desorden: tarde o temprano querrás **agrupar tus módulos** de la misma manera que  
previamente has agrupado funciones: Existe un contenedor más general que un módulo?  
- Sí lo hay, es un **paquete**: en el mundo de los módulos, un paquete juega un papel similar al de una carpeta o directorio en el  
mundo de los archivos.  
  
  
## **Tu primer módulo: paso 1**  
  
En esta sección, trabnajarás localmente en tu máquina. Comencemos desde cero. Crea un archivo vacío, de la siguiente manera:  
  
![moduloprimerpaso](../img/moduloprimerpaso.jpg)  
  
Se necesitan dos archivos para realizar estos experimentos. Uno de ellos será el *módulo* en sí. Está vacío ahora. No te preocupes, lo  
vas a llenar con código pronto.  
  
El archivo lleva por nombre *module.py*. No muy creativo, pero es simple y claro.  
  
  
## **Tu primer módulo: paso 2**  
  
El segundo archivo contiene el código que utiliza el nuevo módulo. Su nombre es *main.py*. Su contenido es muy breve hasta ahora:  
  
![modulosegundopaso](../img/modulosegundorpaso.jpg)  
  
Nota: **ambos archivos deben estar ubicados en la misma carpeta**. Te recomendamos crear una carpeta nueva y vacía para ambos  
archivos. Esto hará que las cosas sean más fáciles.  
  
Inicia el IDLE (o cualquier otro que prefieras) y ejecuta el archivo *main.py*. Qué es lo que ves?  
  
No deberías ver nada. Esto significa que Python a importado con éxito el contenido del archivo module.py.  
  
No importa que el módulo esté vacío por ahora. El primer paso ya está hecho, pero antes de dar el siguiente paso, queremos que  
eches un vistazo a la carpeta en la que se encuentran ambos archivos.  
  
Notas algo interesante?  
  
Ha aparecido una nueva subcarpeta, puedes verla? su nombre es __pycache__. Echa un vistazo adentro. Qué es lo que ves?  
  
Hay un archivo llamado (más o menos) *module.cpython-xy.pcy* donde *x* y *y* son dígitos derivados de tu versión de Python (por  
ejemplo, serán *3* y *8* si utilizas Python 3.8).  
  
El nombre del archivo es el mismoq ue el de tu módulo. La parte posterior al primer punto dice qué implementación de Python ha  
creado el archivo (*CPython*) y su número de versión. La ultima parte (pyc) viene de las palabras *Python* y *compilado*.  
  
Puedes mirar dentro del archivo: el contenido es completamente ilegible para los humanos. Tiene que ser así, ya que el archivo está  
destinado solo para el uso de Python.  
  
Cuando Python importa un módulo por primera vez, **traduce el contenido a una forma algo compilada**.  
  
El archivo no contiene código en lenguaje máquina: es **código semi-compilado** interno de Python, listo para ser ejecutado por el  
intérprete de Python. Como tal archivo no requiere tantas comprobaciones como las de un archivo fuente, la ejecución comienza más  
rápido y también se ejecuta más rápido.  
  
Gracias a eso, cada importación posterior será más rápida que interpretar el código fuente desde cero.  
  
Python puede verificar si el archivo fuente del módulo ha sido modificado (en este caso, el archivo *pyc* será reconstruido) o no  
(cuando el archivo *pyc* pueda ser ejecutado al instante). Este proceso es completamente automático y transparente, no tiene que ser  
tomado en cuenta.  
  
  
## **Tu primer módulo: paso 3**  
  
Ahora hemos puesto algo en el archivo del módulo:  
  
![tercerpasomodulo](../img/tercerpasomodulo.jpg)  
  
Puedes notar alguna diferencia entre un módulo y un script ordinario? No hay ninguna hasta ahora.  
  
Es posible ejecutar este archivo como cualquier otro script. Pruébalo por ti mismo.  
  
Qué es lo que pasa? deberías ver la siguiente línea dentro de tu consola:  
  
```
Me gusta ser un módulo.
```  
  
## **Tu primer módulo: paso 4**  
  
Volvamos al archivo *main.py*  
Ejecuta el archivo. Qué ves? Con suerte veras algo como esto:  
```
Me gusta ser un módulo.
```  
  
Qué significa realmente?  
  
Cuando un módulo es importado, su contenido es **ejecutado impliícitamente por Python**. Le da al módulo la oportunidad de  
inicializar algunos de sus aspectos internos (por ejemplo, puede asignar a algunas variables valores útiles).  
  
Nota: la **inicialización se realiza sólo una vez**. Cuando se produce la primera importación, por lo que las asignaciones realizadas por  
el módulo no se repiten innecesariamente.  
  
Imagina el siguiente contexto:  
  
- Existe un módulo llamado *mod1*.
- Existe un módulo llamado *mod2* el cual contiene la instrucción ```import mod1```.  
- Hay un archivo principal que contiene las instrucciones