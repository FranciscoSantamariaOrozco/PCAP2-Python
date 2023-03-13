# **Procesando archivos**  

<br></br>  

## **Accediendo archivos desde código en Python**    
Uno de los problemas más comunes en el trabajo del desarrollador es **procesar datos almacenados en archivos** que generalmente  
se almacenan físicamente utilizando dispositivos de almacenamiento: discos duros, ópticos, de red o de estado sólido.  

Es fácil imaginar un programa que clasifique 20 números, y es igualmente fácil imaginar que el usuario de este programa ingrese estos  
veinte números directamente desde el teclado.  

Es mucho más difícil imaginar la misma tarea cuando hay 20,000 números para ordenar, y no existe un solo usuario que pueda  
ingresar estos números sin cometer un error.  

Es mucho más facil imaginar que estos números se almacenan en el archivo que lee el programa. El programa clasifica los números y  
no los envía a la pantalla, sino que crea un nuevo archivo y guarda la secuencia ordenada de números allí.  

Si queremos implementar una base de datos simple, la única forma de almacenar la información entre ejecuciones del programa es  
guardarla en un archivo (o archivos si tu base de datos es más compleja).  

Es un principio que cualquier problema de programación no simple se basa en el uso de archivos, ya sea que procese imágenes  
(almacenadas en archivos), multiplique matrices (almacenadas en archivos) o calcule salarios e impuestos (lectura de datos  
almacenados en archivos).  

<p align="center">
<img src="img/almacenamientodedatos.jpg">
</p>  

Puedes preguntarte por que hemos esperado hasta ahora para mostrarte esto.  

La respuesta es muy simple: la forma en que Python accede y procesa los archivos se implementa utilizando un conjunto consistente  
de objetos. No hay mejor momento para hablar de esto.  

<br></br>  


## **Nombres de archivos**  
Los diferentes sistemas operativos pueden tratar los archivos de diferentes maneras. Por ejemplo, Windows usa cona convención de  
nomenclatura diferente a la adoptada en los sistemas Unix/Linux.  

Si utilizamos la noción de un nombre de archivo canónico (un nombre que define de forma exclusiva la ubicación del archivo,  
independientemente de su nivel en el árbol de directorios), podemos darnos cuenta de que estos nombres se ven diferentes en  
Windows y en Unix/Linux:  

<p align="center">
<img src="img/rutasdearchivos.jpg">
</p>  

Como puedes ver, los sistemas derivados de Unix/Linux no usan la letra de la unidad de disco (por ejemplo, ```C:```) y todos los  
directorios crecen desde un directorio raíz llamado ```/```, mientras que los sistemas Windows reconocen el directorio raíz como ```\```.  

Además, los nombres de archivo de sistemas Unix/Linux distinguen entre mayúsculas y minúsculas. Los sistemas Windows almacenan  
mayúsculas y minúsculas en el nombre de archivo, pero no distinguen entre ellas.  

Esto significa que estas dos cadenas: ```EsteEsElNombreDelArchivo``` y ```esteeselnombredelarchivo```  describen dos archivos  
diferentes en sistemas Unix/Linux, pero tienen el mismo nombre para un solo archivo en sistemas Windows.  

La diferencia principal y más llamativa es que debes usar **dos separadores diferentes para los nombres de directorio**: ```\``` en  
Windows y ```/``` en Unix/Linux.  

Esta diferencia no es muy importante para el usuario normal, pero es **muy importante al escribir programas en Python**.  

Para entender por qué, intenta recordar el papel muy específico que desempeña ```\``` dentro de las cadenas en Python.  

<br></br>  


## **Nombres de archivos: continuación**  
Supongamos que estás interesado en un archivo en particular ubicado en el directorio *dir*, y con el nombre de *file*  

Supongamos también que deseas asignar a una cadena el nombre del archivo.  

En sistemas Unix/Linux, sería de la siguiente manera:  
```
name = "/dir/file"
```  
<br></br>

Pero si intentas codificarlo para el sistema Windows:  
```
name = "\dir\file"
```  
Obtendrás una sorpresa desagadable: Python generará un error o la ejecución del programa se comportará de manera extraña.  
como si el nombre del archivo se hubiera distorsionado de alguna manera.  

De hecho, no es extraño en lo absoluto, pero es bastante obvio y natural. Python usa la ```\``` como un carácter de escape (como ```\n```).  

Esto significa que los nombres de archivo de Windows deben escribirse de la siguiente manera:  
```
name = "\\dir\\file"
```  

Afortunadamente, también hay una solución más. Python es lo suficientemente inteligente como para poder convertir diagonales en  
diagonales invertidas cada vez que descubre que el sistema operativo lo requiere.  

Esto significa que cualquiera de las siguientes asignaciones:  
```
name = "/dir/file"
name = "c:/dir/file"
```  
Funcionarán también con Windows.  

Cualquier programa escrito en Python (y no solo en Python, porque esa convención se aplica a practicamente todos los lenguajes de  
programación) no se comunica con los archivos directamente, sino a través de algunas entidades abstractas que se nombran de  
manera diferente en los distintos lenguajes o entornos, los términos más utilizados son **handles o manejadores (un tipo de puntero**  
**inteligente)** o **streams (una especie de canal)** (los usaremos como sinónimos aquí).  

El programador, que tiene un conjunto de funciones y métodos, puede realizar ciertas operaciones en el stream, que afectan los  
archivos reales utilizando mecanismos contenidos en el núcleo del sistema operativo.  

De esta forma, puedes implementar el proceso de acceso a cualquier archivo, incluso cuando el nombre del archivo es desconocido al  
momento de escribir el programa.  

Las operaciones realizadas con el stream abstracto reflejan las actividades relaccionadas con el archivo físico.  

<p align="center">
<img src="img/accesoarchivos.jpg">
</p>  

Para conectar (vincular) el stream con el archivo, es necesario realizar una operación explícita.  

La operación de conectar un stream con un archivo es llamada **abrir el archivo**, mientras que desconectar el enlace se denomina  
```cerrar el archivo```.  

Por lo tanto, la conclusión es que la primera operación realizada en el stream es siempre ```open (abrir)``` y la ultima es ```close```  
```cerrar```. El programa, en efecto, es libre de manipular el stream entre estos dos eventos y manejar el archivo asociado.  

Esta libertad está limitada por las características físicas del archivo y la forma en que se abrió el archivo.  

Digamos nuevamente que la apertura del stream puede fallar, y puede ocurrir debido a varias razones: la más común es la falta de un archivo con un nombre específico.  

También puede suceder que el archivo físico exista, pero el programa no puede abrirlo. También existe el riesgo de que el programa  
haya abierto demasiados streams, y el sistema operativo específico puede no permitir la apertura simultánea de más de *n* archivos  
(por ejemplo, 200).  

Un programa bien escrito debe detectar estas aperturas fallidas y reaccionar en consecuencia.  

<br></br>  


## **Archivos: streams**  
La apertura del stream no solo está asociada con el archivo, sino que también se debe declarar la manera en que se procesará el  
stream. Esta delcaración se llama **open mode (modo de apertura)**.  

Si la apertura es exitosa, el **programa solo podrá realizar las operaciones que sean consistentes con el modo abierto declarado**.  

Hay dos operaciones básicas a realizar con el stream:  

- **Lectura** del stream: las porciones de las datos de recuperan del archivo y se colocan en un área de memoria administrada por el  
programa (por ejemplo, una variable).  
- **Escritura** del stream: Las porciones de los datos de la memoria (por ejemplo, una variable) se transfieren al archivo.  

Hay tres modos básicos para abrir un stream:  

- **Modo lectura**: un stream abierto en este modo permite **solo operaciones de lectura**; intentar escribir en la transmisión  
provocará una excepción (la excepción se llama *UnsupportedOperation**, la cual hereda el *OSError* y el *ValueError*, y proviene  
del módulo *io*).  

- **Modo Escritura**: un stream abierto en este modo permite **solo operaciones de escritura**; intentar leer el stream provocará la  
excepción mencionada anteriormente.  

- **Modo Actualizar**: un stream abierto en este modo permite **tanto lectura como escritura**.  

Antes de discurtir como manipular los streams, te debemos una explicación. **El stream se comporta casi como una grabadora**.  

Cuando lees algo de un stream, un cabezal virtual se mueve sobre la transmisión de acuerdo con el número de bytes transferidos  
desde el stream.  

Cuando escribes algo en el stream el mismo cabezal se mueve a lo largo del stream registrando los datos de la memoria.  

Siempre que hablemios de leer y escribir en el stream, trata de imaginar esta analogía. Los libros de programación se refieren a este  
mecanismo como la **posición actual del archivo**, aquí también usaremos este término.  

<p align="center">
<img src="img/conceptoreadwrite.jpg">
</p>  

Ahora es necesario mostrarte el objeto responsable de representar los streams en los programas.  

<br></br>  


## **Manejo de archivos**  
Python supone que **cada archivo está oculto detrás de un objeto de una clase adecuada**.  

Por supuesto, es difícil no preguntar cómo interpretar la palabra *adecuada*.  

Los archivos se pueden procesar de muchas maneras diferentes: algunos dependen del contenido del archivo, otros de las intenciones  
del programador.  

En cualquier caso, diferentes archivos pueden requerir diferentes conjuntos de operaciones y comportarse de diferentes maneras.  

Un objeto de una clase adecuada es **creado cuando abres el archivo y lo aniquilas al momento de cerrarlo**.  

Entre estos dos eventos, puedes usar el objeto para especificar que operaciones se deben realizar en un stream en particular. Las  
Operaciones que puedes usar están impuestas por **la forma en que abriste el archivo**.  

En general, el objeto proviene de una de las clases que se muestran aquí:  

<p align="center">
<img src="img/origenobjetos.jpg">
</p>  

Nota: nunca se utiliza el constructor para dar vida a estos objetos. La única forma de **obtenerlos es invocar la función llamada**  
```open()```  

La funcioón analiza los argumentos proporcionados y crea automáticamente el objeto requerido.  

Si deseas **deshacerte del objeto, invoca el método denominado** ```close()```.  

La invocación cortará la conexión con el objeto y el archivo, y eliminará el objeto.  

Para nuestros propósitos, solo nos ocuparemos de los streams representados por los objetos ```BufferIOBase``` y ```TextIOBase``.  
Entenderás por que pronto.  

<br></br>  


## **Manejo de archivos: continuación**  
Debido al tipo de contenido de los streams, **todos se dividen en tipo texto y binario**.  

Los streams de texto están estructurados en líneas; es decir, contienen caracteres tipográficos (letras, dígitos, signos de puntuación,  
etc.) dispuestos en filas (líneas), como se ve a simple vista cuando se mira el contenido del archivo en el editor.  

Ese tipo de archivo es escrito (o leído) principalmente carácter por carácter, o línea por línea.  

Los streams binarios no contienen texto, sino una secuencia de bytes de cualquier valor. Esta secuencia puede ser, por ejemplo, un  
programa ejecutable, una imagen, un audio o un videoclip, un archivo de base de datos, etc.  

Debido a que estos archivos no contienen líneas, las lecturas y escrituras se relacionan con porciones de datos de cualquier tamaño.  
Por lo tanto, los datos se leen y escriben byte a byte, o bloque a bloque, donde el tamaño del bloque generalmente varía de uno a un  
valor elegido arbitrariamente.  

Ahora viene un problema pequeño. En los sistemas Unix/Linux, los extremos de la línea están marcados por un solo carácter llamado  
```LF``` (Código ASCII 10) designado en los programas de Python como ```\n```.  

Otros sistemas operativos, especialmente los derivados del sistema prehistórico CP/M (que también aplica a los sistemas de la familia  
Windows) utilizan una convención diferente: el final de la línea está marcada por un par de caracteres, ```CR``` y ```LF``` (códigos ASCII 13 y  
10) los cuales se pueden codificar como ```\r\n```.  

Esta ambigüedad puede causar varias consecuencias desagradables.  

Si creas un programa responsable de procesar un archivo de texto y está escrito para Windows, puedes reconocer los extremos de las  
líneas al encontrar los caracteres ```\r\n```, pero si el mismo programa se ejecuta en un entorno Unix/Linux será completamente inútil,  
y viceversa: el programa escrito para sistemas Unix/Linux podría ser inutil en Windows.  

Estas característiccas indeseables del programa, que impiden o dificultan el uso del programa en diferentes entornos, se denomina  
**falta de portabilidad**.  

Del mismo modo, el rasgo del programa que permite la ejecución en diferentes entornos se llama **portabilidad**. Un programa dotado  

de tal rasgo se llama **programa portable**.  

<br></br>  


## **Manejo de archivos: continuación**  
Dado que los problemas de portabilidad eran (y siguen siendo) muy graves, se tomó la decisión de resolver definitivamente el  
problema de una manera que no atraiga mucho la atención del desarrollador.  

<p align="center">
<img src="img/binariotexto.jpg">
</p>  

Se realizó a nivel de clases, que son responsables de leer y escribir caracteres hacia y desde el stream. Funciona de la siguiente  
manera:  

- Cuando el stream está abierto y se recomienda que los datos en el archivo asociado se procesen como texto (o no existe tal  
aviso), se **cambia al modo texto**.  

- Durante la lectura y escritura de líneas desde y hacia el archivo asociado, no ocurre nada especial en el entorno Unix, pero  
cuando se realizan las mismas operaciones en el entorno Windows, un proceso llamado **traducción de caracteres de nueva**  
**línea** ocurre: cuando lees una línea del archivo, cada par de caracteres ```\r\n``` se reemplaza con un sólo carácter ```\n```, y  
viceversa; durante las operaciones de escritura, cada carácter ```\n``` se reemplaza con un par de caracteres ```\r\n```.  

- El mecanismo es completamente **transparente** para el programa, el cual puede escribirse como si estuviera destinado a  
procesar archivos de texto Unix/Linux solamente; el código fuente ejecutado en un entorno Windows también funcionará  
correctamente.  

- Cuando el stream está abierto, su contenido se toma tal cual es, **sin ninguna conversión** - no se agregan, ni se omiten bytes.  

<br></br>  


## **Abriendo los streams**  
El **abrir un stream** se realiza mediante una función que se puede invocar de la siguiente manera:  
```python
stream = open(file, mode = 'r', encoding = None)
```  

Vamos a analizarlo:  

- El nombre de la función(```open```) habla por si mismo; si la apertura es exitosa, la función devuelve un objeto stream; de lo  
contrario, se genera una excepción (por ejemplo, *FileNotFoundError* **si el archivo que vas a leer no existe**).  

- El primer parámetro de la función (```file```) especifica el nombre de archivo que se asociará al stream.  

- El segundo parámetro (```mode```) especifica el modo de apertura utilizado para el stream; es una cadena llena de una secuencia de  
caracteres, y cada uno de ellos tiene su propio significado especial (más detalles pronto).  

- El tercer parámetro (```encoding```) especifica el tipo de codificación (por ejemplo, UTF-8 cuando se trabaja con archivos de texto).  

- La apertura debe ser la primera operación realizada en el stream.  

Nota: el modo y los argumentos de codificación pueden omitirse; en dado caso, se tomarán sus valores predeterminados. El modo de  
apertura predeterminado es leer en modo de texto, mientras que la codificación predeterminada depende de la plataforma utilizada.  

Permítenos ahora presentarte los modos de apertura más importantes y útiles. Listo?  

<br></br>  


## **Modos para abrir los streams**  
```r``` modo de apertura: lectura  
- El stream será abierto en **modo lectura**.  
- El archivo asociado con el stream **debe existir** y tiene que ser legible, de lo contrario la función ```open()``` generará una  
excepción.  
<br></br>

```w``` modo de apertura: escritura  
- El stream será abierto en **modo escritura**.  
- El archivo asociado con el stream **no necesita existir**. Si no existe, se truncará a la longitud de cero (se borra);  
si la creación no es posible (por ejemplo, debido a permisos del sistema), la función ```open()``` generará una excepción.  
<br></br>

```a``` modo de apertura: adjuntar  
- El stream será abierto en **modo adjuntar**.  
- El archivo asociado con el stream **no necesita existir**; si no existe, se creará; si existe, el cabezal de grabación virtual se  
establecerá al final del archivo (el contenido anterior del archivo permanece intacto).  
<br></br>

```r+``` modo de apertura: lectura y actualización  
- El stream será abierto en **modo adjuntar**.  
- El archivo asociado con el stream **debe existir y tiene que permitir escritura**, de lo contrario la función ```open()``` generará una  
excepción.  
- Se permiten operaciones de lectura y escritura en el stream.  
<br></br>

```w+``` modo de apertura: escritura y actualización  
- El stream será abierto en **modo escritura y actualización**.  
- El archivo asociado con el stream **no necesita existir**; si no existe, se creará; el contenido anterior del archivo permanece  
intacto.  
- Se permiten operaciones de lectura y escritura en el stream.  

<br></br>  


## **Seleccionando modo de texto y modo binario**  
Si hay una letra ```b``` al final de la cadena del modo significa que el stream se debe abrir en el **modo binario**.  

Si la cadena del modo termina con una letra ```t``` el stream es abierto en **modo texto**.  

El modo texto es el comportamiento predeterminado que se utiliza cuando no se especifica ya sea modo binario o texto.  

Finalmente, la apertura exitosa del archivo establecerá la posición actual del archivo (el cabezal virtual de lectura/escritura) antes del  
primer byte del archivo **si el modo no es ```a```** y después del último byte del archivo **si el modo es ```a```**.  
<br></br>
<table align=center>
    <tr>
        <td><b>Modo texto</b></td>
        <td><b>Modo binario</b></td>
        <td><b>Descripción</b></td>
    </tr>
    <tr>
        <td><code>rt</code></td>
        <td><code>rb</code></td>
        <td>lectura</td>
    </tr>
    <tr>
        <td><code>wt</code></td>
        <td><code>wb</code></td>
        <td>escritura</td>
    </tr>
    <tr>
        <td><code>at</code></td>
        <td><code>ab</code></td>
        <td>adjuntar</td>
    </tr>
    <tr>
        <td><code>r+t</code></td>
        <td><code>r+b</code></td>
        <td>lectura y actualización</td>
    </tr>
    <tr>
        <td><code>w+t</code></td>
        <td><code>w+b</code></td>
        <td>escritura y actualización</td>
    </tr>
</table>  

También puedes abrir un archivo para su creación exclusiva. Puedes hacer esto usando el modo de apertura ```x```. Si el archivo ya existe, la función  ```open()``` generará una excepción.  

<br></br>  


## **Abriendo el stream por primera vez**  
Imagina que queremos desarrollar un programa que lea el contenido del archivo de texto llamado:  
*C:Users\User\Desktop\file.txt*.  

Cómo abrir ese archivo para leerlo? aquí está el fragmento del código:  
```python
try:
    stream = open("C:\Users\User\Desktop\file.txt", "rt")
    # El procesamiento va aquí.
    stream.close()
except Exception as exc:
    print("No se puede abrir el archivo:", exc)
```  

Que está pasando aquí?  
- Hemos abierto el bloque try-except ya que queremos manejar los errores de ejecución suavemente.  
- Se emplea la función ```0open()``` para intentar abrir el archivo especificado (ten en cuenta la forma en que hemos especificado el  
nombre del archivo).  
- El modo de apertura se define como texto para leer (como **texto es la configuración predeterminada**, podemos omitir la ```t```  
en la cadena de modo)  
- En caso de éxito obtenemos un objeto de la función ```open()``` y lo asignamos a la variable del stream.  
- Si ```open()``` falla, manejamos la excepción imprimiendo la información completa del error (es bueno saber qué sucedió  
- exactamente).  

<br></br>  


## **Streams pre-abiertos**  
Dijimos anteriormente que cualquier operación del stream debe estar precedida por la invocación de la función ```open()```. Hay tres  
excepciones bien definidas a esta regla.  

Cuando comienza nuestro programa, los tres streams ya están abiertos y no requieren ninguna preparación adicional. Además, tu  
programa puede usar estos streams explícitamente si tienes cuidado de importar el módulo ```sys```:  

```python
import sys
```  

Porque ahí es donde se coloca la declaración de estos streams.  

Los nombres de los streams son: ```sys.stdin```, ```sys.stdout``` y ```sys.stderr```.  

Vamos a analizarlos:  
- ```sys.stdin```
  - *stdin* (significa *entrada estándar*).  
  - El stream ```stdin``` normalmente se asocia con el teclado, se abre previamente para la lectura y se considera como la fuente  
de datos principal para los programas en ejecución.
  -  La función bien conocida ```input()``` lee datos de ```stdin``` por defecto.  

- ```sys.stdout```
  - *stdout* (significa *salida estándar*).  
  - El stream ```stdout``` normalmente está asociado con la pantalla, preabierta para escritura, considerada como el objetivo  
principal para la salida de datos por el programa en ejecución.  
  - La función bien conocida ```print()``` envía los datos al stream ```stdout```.  

- ```sys.stderr```  
  - *stderr* (significa *salida de error estándar*)  
  - El stream ```stderr``` normalmente está asociado con la pantalla, preabierta para escribir, considerada como el lugar  
principal donde el programa en ejecución debe enviar información sobre los errores encontrados durante su trabajo.  
  - No hemos presentado ningún método para enviar datos a este stream (lo haremos pronto, lo prometemos).  
  - La separación de ```stdout``` (resultados útiles producidos por el programa) de ```stderr``` (mensajes de error,  
indudablemente útiles pero no proporcionan resultados) ofrece la posibilidad de redirigir estos dos tipos de información a  
los diferentes objetivos. Una discusión más extensa sobre el tema está más allá del alcance de nuestro curso. El manual  
del sistema operativo proporcionará más información sobre estos temas.  

<br></br>  


## **Cerrando streams**  
La última operación realizada en un stream (esto no incluye a los streams ```stdin```, ```stdout```, y ```stderr``` pues no lo requieren) debe  
ser **cerrarlo**.  

Esta acción se realiza mediante un método invocado desde dentro del objeto del stream: ```stream.close()```.  
- El nombre de la función es fácil de entender ```close()```, es decir, cerrar.  
- La función no espera argumentos; el stream no necesita estar abierto.  
- La función no devuelve nada pero genera una excepción *IOError* en caso de un error.  
- La mayoría de los desarrolladores creen que la función ```close()``` siempre tiene éxito y, por lo tanto, no hay necesidad de  
verificar si ha realizado su tarea correctamente.  

Esta creencia está solo parcialmente justificada. Si el stream se abrió para escribir y luego se realizó una serie de operaciones de  
escritura, puede ocurrir que los datos enviados al stream aún no se hayan transferido al dispositivo físico (debido a los  
mecanismos de **caché** o **buffer**). Dado que el cierre del stream obliga a los buffers a descargarse, es posible que dichas descargas  
fallen y, por lo tanto, ```close()``` falle también.  

Ya hemos mencionado fallas causadas por funciones que operan con los streams, pero no mencionamos nada sobre cómo podemos  
identificar exactamente la causa de la falla.  

La posibilidad de hacer un diagnóstico existe y es proporcionada por uno de los componentes de excepción de los streams.  
Hablaremos acerca de ellos a continuación.  

<br></br>  


## **Diagnosticando problemas con los streams**  
El objeto ```IOError``` está equipado con una propiedad llamada ```errno``` (el nombre viene de la frase *error number*, número de error)  
y puedes accederla de la siguiente manera:  
```python
try:
    # Algunas operaciones con streams.
except IOError as exc:
    print(exc.errno)
```  

El valor del atributo ```errno``` se puede comparar con una de las constantes simbólicas predefinidas en el módulo ```errno```.  

Echemos un vistazo a algunas **constantes seleccionadas útiles para detectar errores en los streams**:  
- ```errno.EACCES``` -> *Permiso denegado*  
El error se produce cuando intentas, por ejemplo, abrir un archivo con atributos de *solo lectura* para editarlo.  

- ```errno.EBADF``` -> *Número de archivo incorrecto*  
El error se produce cuando intentas, por ejemplo, operar un stream sin abrirlo.  

- ```errno.EEXIST``` -> *Archivo existente*  
El error se produce cuando intentas, por ejemplo, cambiar el nombre de un archivo con su nombre anterior.  

- ```errno.EFBIG``` -> *Archivo demasiado grande*  
El error ocurre cuando intentas crear un archivo que es más grande que el máximo permitido por el sistema operativo.  

- ```errno.EISDIR``` -> *Es un directorio*  
El error se produce cuando intentas tratar un nombre de directorio como el nombre de un archivo ordinario.  

- ```errno.EMFILE``` -> *Demasiados archivos abiertos*  
el error se produce cuando intentas abrir simultáneamente más streams de los aceptables para el sistema operativo.  

- ```errno.ENOENT``` -> *El archivo o directorio no existe*  
El error se produce cuando intentas acceder a un archivo o directorio inexistente.  

- ```errno.ENOSPC``` -> *No queda espacio en el dispositivo*  
El error ocurre cuando no hay espacio libre en el dispositivo.  

La lista completa es mucho más larga (incluye también algunos códigos de error no relaccionados con el procesamiento de los  
streams).  

<br></br>  


## **Diagnosticando problemas con los streams**  
Si eres un programador muy cuidadoso, puedes sentir la necesidad de usar una secuencia de sentencias similar  
a las que se te presentan en el editor:  
```python
import errno

try:
    s = open("c:/users/user/Desktop/file.txt", "rt")
    # El procesamiento va aquí.
    s.close()
except Exception as exc:
    if exc.errno == errno.ENOENT:
        print("El archivo no existe.")
    elif exc.errno == errno.EMFILE:
        print("Demasiados archivos abiertos.")
    else:
        print("El numero del error es:", exc.errno)
```  

Afortunadamente, existe una función que puede **simplificar el código de manejo de errores**.  

Su nombre es ```strerror()```, y proviene del módulo ```os``` y **espera solo un argumento: un número de error**.  

Su función es simple: proporciona un número de error y una cadena que describe el significado del error.  

Nota: si pasas un código de error inexistente (un número que no está vinculado a ningún error real), la función  
generará una excepción *ValueError*.  

Ahora podemos simplificar nuestro código de la siguiente manera:  
```python
from os import strerror

try:
    s = open("c:/users/user/Desktop/file.txt", "rt")
    # El procesamiento va aquí.
    s.close()
except Exception as exc:
    print("El archivo no pudo ser abierto:", strerror(exc.errno))
```  

Bueno. Ahora es el momento de tratar con archivos de texto y familiarizarse con algunas técnicas básicas que  
puedes utilizar para proecesarlos.  

<br></br>  


## **Puntos clave**  
1. Un archivo necesita ser **abierto** antes de que pueda ser procesado por un programa, y debe ser **cerrado** cuando el procesamiento  
termine.  
<br>
El abrir un archivo lo asocia con el **stream**, que es una representación abstracta de los datos físicos almacenados en los medios. La  
forma en que se procesa el stream se llama **modo de apertura**. Existen **tres** modos de apertura:  
- **modo lectura**: solo se permiten operaciones de lectura.
- **modo escritura**: solo se permiten operaciones de escritura.
- **modo de actualización**: se permiten ambas, lectura y escritura.  
<br></br>  

2. Dependiendo del contenido del archivo físico, se pueden usar diferentes clases de Python para procesar archivos. En general,  
```BufferedIOBase``` es capaz de procesar cualquier archivo, mientras que ```TextIOBase``` es una clase especializada dedicada al  
procesamiento de archivos de texto (es decir, archivos que contienen textos visibles para humanos divididos en líneas usando  
marcadores de nueva línea). Por lo tanto, los streams se pueden dividir en **binarios** y de **texto**.  
<br></br>  

3. Las siguientes sintaxis de la función ```open``` se utilizan para abrir un archivo: 
```
open(nombre_archivo, modo=modo_apertura, codificación=codificacion_de_texto)
```
la invocación crea un objeto stream y lo asocia con el archivo llamado ```nombre_archivo```, utilizando el modo ```modo_apertura``` y  
configurando la especificada ```codificacion_de_texto```, o **genera una excepción en caso de un error**.  
<br></br>  

4. Los tres streams **predefinidos** que ya estan abiertos cuando inicia el programa son:  
- ```sys.stdin```  -> entrada estándar.
- ```sys.stdout``` -> salida estándar.
- ```sys.stderr``` -> salida de error estándar.  
<br></br>   

5. El objeto de la excepción ```IOError```, creado cuando cualquier operación de archivo falla (incluyendo las operaciones de apertura),  
contiene una propiedad llamada ```errno```, que contiene el código de finalización de la acción fallida. Utiliza este valor para diagnosticar  
el problema.  

<br></br>

#  
[Ejercicios](/Modulo4/Seccion2/Sec2-ej.md)
<br></br>

[Soluciones](/Modulo4/Seccion2/Sec2-ejsol.md)  

#

[Volver a: Módulo 4 - Miscelaneo](../README.md)