# Fundamentos de Python 2
## Módulo 1
**Módulos, Paquetes y Pip**

En este módulo, aprenderás como:  

- Importar y usar módulos de Python.
- Emplear algunos de los módulos más útiles de la biblioteca estándar de Python.
- Construir y usar paquetes de Python.
- PIP (Instalador de Paquetes de Python) y cómo usarlo para instalar y desinstalar  
paquetes listos para usar de PyPI.  
  
  
## Qué es un módulo?
  
El código de computadora tiene una tendencia a crecer. Podemos decir que el código que no crece probablemente sea completamente  
inutilizable o esté abandonado. Un código real, deseado y ampliamente utilizado se desarrolla continuamente, ya que tanto las  
demandas de los usuarios como sus expectativas se desarrollan de manera diferente.  
  
Un código que no puede responder a las necesidades de los usuarios se olvidará rápidamente y se reemplazará instantáneamente con  
un código nuevo, mejor y más flexible. Se debe esta preparado para esto, y nunca pienses que tus programas están terminados por  
completo. La finalización es un estado de transición y generalmente pasa rápidamente, después del primer informe de error. Python  
en sí es un buen ejemplo de cómo actúa esta regla.  

El código creciente es, de hecho, un problema creciente. Un código más grande siempre significa un mantenimiento más difícil. La  
búsqueda de errores siempre es más fácil cuando el código es más pequeño (al igual que encontrar una rotura mecánica es más  
simple cuando la maquinaria es más simple y pequeña).  

Además, cuando se espera que el código que se está creando sea realmente grande (puedes usar el número total de líneas de código  
como una medida útil, pero no muy precisa, del tamaño del código) entonces, se deseará, o más bien, habrá la necesidad de dividirlo  
en muchas partes, implementando en paralelo por unos cuantos, una docena, varias docenas o incluso varios cientos de  
desarrolladores.  

Por supuesto, esto no se puede hacer usando un archivo fuente grande, el cual esta siendo editado por todos los programadores al  
mismo tiempo. Esto seguramente conducirá a un desastre.  

Si se desea que dicho proyecto de software se complete con éxito, se deben tener los medios que permitan:  
  
- Dividir todas las tareas entre los desarrolladores.
- Después, unir todas las partes creadas en un todo funcional.  
  
Por ejemplo, un determinado proyecto se puede dividir en dos partes principales:  
  
- La interfaz de usuario (la parte que se comunica con el usuario mediante widgets y una pantalla gráfica).  
- La lógica (la parte que procesa los datos y produce resultados).  
  
Cada una de estas partes se puede (muy probablemente) dividir en otras más pequeñas, y así sucesivamente. Tal proceso a menudo  
se tenomina **descomposición**.  
  
Por ejemplo, si te pidieran organizar una boda, no harías todo tu mismo: encontrarías una serie de profesionales y dividirías la tarea  
entre todos.  
  
Cómo se divide una pieza de software en partes separadas pero cooperantes? Esta es la pregunta. Los **módulos** son la respuesta.