## **El ecosistema de paquetes de Python y cómo usarlo**  
  
Python es un instrumento muy poderoso: esperamos que ya lo hayas experimentado. Muchas personas de todo el mundo se sienten  
así y usan Python de forma regular para desarrollar lo que pueden hacer en muichos campos de actividad completamente diferentes.  
Esto significa que Python se ha convertido en una **herramienta interdisciplinaria** empleada en innumerables aplicaciones. No  
podemos pasar por todas las esferas en las que Python brillantemente muestra sus habilidades, así que permítenos contarte las más  
impresionantes.  
  
En primer lugar, Python se ha convertido en líder en investigación sobre inteligencia artificial. La minería de datos, una de las  
disciplinas científicas modernas más prometedoras, también utiliza Python. Matemáticos, psicólogos, genetistas, meteorólogos,  
lingüistas: todas estas personas ya usan Python, o si aún no lo hacen, estamos seguros de que lo harán muy pronto. No hay forma de  
escapar de esa tendencia.  

Por supuesto, no tiene ningún sentido hacer que todos los usuarios de Pyton escriban su código desde cero, manteniéndolos  
perfectamente aislados del mundo exterior y de los logros de otros programadores. Esto ser+ia antinatural y contraproducente.  
  
Lo más preferible y eficiente es permitir que todos los miembros de la comunidad de Python intercambien librement sus códigos y  
experiencias. En este modelo, nadie está obligado a empezar a trabajar desde cero, ya que existe una alta probabilidad de que alguien  
más haya estado trabajando en el mismo problema (o en uno muy similar).  
  
Como sabes, Python se creó como software de código abierto, y esto también funciona como una invitación para que todos los  
programadores mantengan todo el ecosistema de Python como un entorno abierto, amigable y libre. Para que el modelo funcione y  
evolucione, se deben proporcionar algunas herramientas adicionales, herramientas que ayuden a los creadores a publicar, mantener y  
cuidar su código.  
  
Estas mismas herramientas deberían ayudar a los usuarios a hacer uso del código, tanto el código ya existente como el código nuevo  
que aparece todos los días. Gracias a eso, escribir código nuevo para nuevos desafíos no es como construir una casa nueva,  
comenzando por los cimientos.  
  
Además, el programador es libre de modificar el código de otra persona para adaptarlo a sus propias necesidades y, de hecho, crear  
un producto completamente nuevo que pueda ser utilizad por otro desarrollador. Afortunadamente, el proceso parece no tener fin.  
  
Para hacer girar este mundo, se deben establecer y mantener en movimiento dos entidades básicas: **un repositorio centralizado** de  
todos los paquetes de software disponibles; y una herramienta que permite a los usuarios **acceder al repositorio**. Ambas entidades  
ya existen y se pueden utilizar en cualquier momento.  
  
## **El ecosistema de paquetes de Python y cómo usarlo**  
  
El repositorio (o *repo* para abreviar) que mencionamos se llama **PyPI** (es la abreviatura de Python Package Index) y lo mantiene un  
grupo de trabajo llamado Packaging Working Group, una parte de la Python Software Foundation, cuya tarea principal es apoyar a los  
desarroladores de Python en la diseminación de código eficiente.  
  
Puedes encontrar su sitio web aquí:  
![https://wiki.python.org/psf/PackagingWG](https://wiki.python.org/psf/PackagingWG)  
  
El sitio web de PyPI (administrado por PWG) se encuentra en la dirección:  
![https://pypi.org/](https://pypi.org/)  
  
En Julio de 2021 fuimos al sitio mencionado, y descubrimos que PyPI albergaba 315,000 proyectos, ue constan de más de 4,500,000  
archivos administradors por 520,000 usuarios.  
  
Estos tres números por sí solos muestran claramente la potencia de la comunidad de Python y la importancia de la cooperación entre  
desarrolladores.  
  
Debemos señalar que PyPI no es el único repositorio de Python existente. Por el contrario, hay mucos de ellos, creados para  
proyectos y dirigidos por muchas comunidades Python más grandes y más pequeñas. Es probable que algún día tu y tus colegas  
quieran **crear sus propios repositorios**.  
  
De todos modos, PyPI es el repositorio de Python más importante del mundo. Si modificamos un poco el dicho clásico, podemos  
afirmar que "todos los caminos de Python conducen a PyPI", y eso no es una exageracion.  
  
## **El repositorio de PyPI: La tienda de quesos**  
  
El repositorio de PyPI a veces se denomina **la tienda de quesos**.  
  
Te suena un poco extraño? No te preocupes, todo es perfectamente inocente.  
  
Nos referimos al repositorio como una tienda, por que vas allí por las mismas razones por las que vas a otras tiendas: para satisfacer  
tus necesidades. Si quieres un poco de queso, ve a la quesería. Si deseas una pieza de software, ve a la tienda de software.  
Afortunadamente, la analogía termina aquí: no necesitas dinero para sacar algún software de la tienda de repositorios.  
  
PyPI es completamente gratuito, puedes tomar un código y usarlo; no encontrarás cajero ni guardia de seguridad. Por supuesto, esto  
no te exime deser cortés y honesto. Debees obedecer todos los términos de la licencia, así que no te olvides de leerlos.  
  
OK, se comprende lo de la tienda, pero qué tiene que ver el queso con Python?  
  
The Chesse Shop (La Tienda de Quesos) es uno de los sketches más famosos de Monty Python. Representa la aventura surrealista de  
un inglés que intenta comprar queso. Desafortunadamente, la tienda que visita (llamada inmodestamente Ye National Chesse   
Emporium) no tiene queso en existencia.  
  
Por supuesto, está destinado a ser irónico. Como ya sabes, PyPI tiene una gran cantidad de software en stock y está disponible las 24  
horas del día, los 7 días de la semana. Tiene todo el derecho a identificarse como **Ye International Python Software Emporium**.  
 
  
## **El Repositorio de PyPI: La Tienda de Quesos (continuación)**  
  
PyPI es una tienda muy específica, no solo porque ofrece todos sus productos de forma gratuita, también requiere una herramienta  
especial para hacer uso de ella.  
  
Afortunadamente, esta herramienta también es gratuita, por lo que si deseas hacer tu propia hamburguesa con queso digital  
utilizando los productos que ofrece PyPI Shop, necesitarás una herramienta gratuita llamada *pip*.  
  
No, no has escuchado mal. Solo *pip*. Es otro acrónimo, claro, pero su naturaleza es más compleja que el PyPI mencionado  
anteriormente, ya que es un ejemplo de acrónimo recursivo, lo que significa que el acrónimo se refiere a sí mismo, lo que significa que  
explicarlo es un proceso infinito.  
  
Por qué? Por que *pip* significa *"pip instala paquetes"*, y el *pip* dentro de *"pip instala paquetes"* significa *"pip instala paquetes"* y...  
  
Detengámonos ahí. Gracias por tu cooperación.  
  
Por cierto, hay algunos otros acrónimos recursivos muy famosos. Uno de ellos es Linux, que se puede interpretar como *"Linux no es*  
*unix"*.  
  
  
## **Cómo instalar *pip***  
  
La pregunta que debería hacerse ahora es: cómo conseguir un cuchillo para un queso específico? En otras palabras, cómo  
asegurarse de que *pip* está instalado y listo para funcionar?  
  
La respuesta más precisa es "depende"  
  
Algunas instalaciones de Python vienen con *pip*, otras no. Además, no solo depende del sistema operativo que utilices, aunque este es  
un factor muy importante.  
  
Comencemos con MS Windows.  
  

