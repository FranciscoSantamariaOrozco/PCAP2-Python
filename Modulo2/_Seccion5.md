## **El cifrado César: encriptando un mensaje**  
  
Te mostraremos cuatro programas simples para presentar algunos aspectos del procesamiento de cadenas en  
Python. Son intencionalmente simples, pero los problemas de laboratorio serán significativamente más  
complicados.  
  
El primer problema que queremos mostrarte se llama **Cifrado César** - más detalles aquí:  
[https://en.wikipedia.org/wiki/Caesar_cipher](https://en.wikipedia.org/wiki/Caesar_cipher)  
  
Este cifrado fue (probablemente) inventado y utilizado por Cayo Julio César y sus tropas durante las Guerras  
Galas. La idea es bastante simple: cada letra del mensaje se reemplaza por su consecuente más cercano (*A* se  
convierte en *B*, *B* se convierte en *C*, y así sucesivamente). La única excepción es la *Z*, la cual se convierte en *A*.  
  
El programa en el editor es una implementación muy simple (pero funcional) del algoritmo.  
```
# Cifrado César.
text = input("Ingresa tu mensaje: ")
cipher = ''
for char in text:
    if not char.isalpha():
        continue
    char = char.upper()
    code = ord(char) + 1
    if code > ord('Z'):
        code = ord('A')
    cipher += chr(code)

print(cipher)
```  
  
Se ha escrito utilizando los siguientes supuestos:  
  
- Solo acepta letras latinas (nota: los Romanos no usaban espacios en blanco ni dígitos).  
- Todas las letras del mensaje está en mayúsculas (nota: los Romanos solo conocían las mayúsculas).  
  

Veamos el código:  
  
- La línea 02: Pide al usuario que ingrese un mensaje (sin cifrar) de una línea.
- La línea 03: Prepara una cadena para el mensaje cifrado (esta vacía por ahora).
- La línea 04: Inicia la iteración a través del mensaje.
- La línea 05: Si el carácter actual no es alfabético...
- La línea 06: ...ignoralo.
- La línea 07: Convierte la letra a mayúsculas (es preferible hacerlo a ciegas, en lugar de verificarlo)
- La línea 08: Obtén el código de la letra e increméntalo en 1.
- La línea 09: Si el código resultante ha "dejado" el alfabeto latino (si es mayor que el código de la Z)...
- La línea 10: ...cámbialo al código de la *A*.
- La línea 11: Agrega el carácter recibido al final del mensaje cifrado.
- La línea 13:  Imprime el cifrado.
  
El código, con este mensaje:  
```
AVE CAESAR
```  
  
Da como salida:
```
BWFDBFTBS
```  
  

## **El cifrado César: descifrando un mensaje**  
  
La operación inversa ahora debería ser clara para ti: solo presentamos el código tal como está, sin ninguna  
explicación.  
  
Observa el código en el editor. Comprueba cuidadosamente si funciona. Usa el criptograma del programa  
anterior.  
```
# Cifrado César - descifrar un mensaje.
cipher = input('Ingresa tu criptograma: ')
text = ''
for char in cipher:
    if not char.isalpha():
        continue
    char = char.upper()
    code = ord(char) - 1
    if code < ord('A'):
        code = ord('Z')
    text += chr(code)

print(text)
```

## **El procesador de números**  
  
El tercer programa muestra un método simple que permite ingresar una línea llena de números y sumarlos  
fácilmente. Nota: la función ```input()```, combinada junto con las funciones ```int()``` o ```float()```, no es lo  
adecuado para este propósito.  
  
El procesamiento será extremadamente fácil: queremos que se sumen los números.  
  
Observa el código en el editor. Analicémoslo.
```
1 |    #Procesador de Números.
2 |
3 |    line = input("Ingresa una línea de números, sepáralos con espacios: ")
4 |    strings = line.split()
5 |    total = 0
6 |    try:
7 |        for substr in strings:
8 |            total += float(substr)
9 |        print("El total es:", total)
10|    except:
11|        print(substr, "no es un numero.")
```  
  
Emplear listas puede hacer que el código sea más pequeño. Puedes hacerlo si quieres.  
  
Presentemos nuestra versión:  
  
- La línea 03: Pide al usuario que ingrese una línea llena de cualquier cantidad de números (los números  
pueden ser flotantes).
- La línea 04: Divide la línea en una lista con subcadenas.
- La línea 05: Se inicializa la suma total a cero.
- La línea 06: Como la conversión de cadena a flotante puede generar una excepción, es mejor continuar con  
la protección del bloque try-except.
- La línea 07: Itera a través de la lista...
- La línea 08: ...e intenta convertir todos sus elementos en números flotantes; si funciona, aumenta la suma.
- La línea 09: Todo está bien hasta ahora, así que imprime la suma.
- La línea 10: El programa termina aquí en caso de error.
- La línea 11: Imprime un mensaje de diagnóstico que muestra al usuario el motivo de la falla.  
  
El código tiene una debilidad importante: muestra un resultado falso cuando el usuario ingresa una línea vacía.  
Puedes arreglarlo?  
  

## **El validador IBAN**  

El cuarto programa implementa (en una forma ligeramente simplificada) un algoritmo utilizado por los bancos  
Europeos para especificar los números de cuenta. El estándar llamado IBAN (Número de cuenta bancaria  
internacional) proporciona un método simple y bastante confiable para validar los números de cuenta contra  
errores tipográficos simples que pueden ocurrir durante la reescritura del número, por ejemplo, de  
documentos en papel, como facturas o facturas en las computadoras.  
  
Puedes encontrar más detalles aquí: [https://en.wikipedia.org/wiki/International_Bank_Account_Number](https://en.wikipedia.org/wiki/International_Bank_Account_Number)  

Un número de cuenta compatible con IBAN consta de:  

- Un código de país de dos letras tomado del estándar ISO 3166-1 (por ejemplo, *FR* para Francia, *GB* para  
Gran Bretaña, *DE* para Alemania, y así sucesivamente).  
- Dos dígitos de verificación utilizados para realizar las verificaciones de validez: pruebas rápidas y simples,  
pero no totalmente confiables, que muestran si un número es inválido (distorsionado por un error  
tipográfico) o válido.  
- El número de cuenta real (hasta 30 caracteres alfanuméricos; la longitud de esa parte depende del país).

El estándar dice que la validación requiere los siguientes pasos (Según Wikipedia):  

- (Paso 1) Verificar que la longitud total del IBAN sea correcta egún el país (este programa no lo hará, pero  
puedes modificar el código para cumplir con este requisito si o deseas; nota: pero debes enseñar al código  
a conocer todas las longitudes utilizadas en Europa).  
- (Paso 2) Mueve los cuatro caracteres iniciales al final de la cadena (es decir, el código del país y los dígitos  
de verificación).  
- (Paso 3) Reemplaza cada letra en la cadena con dos dígitos, expandiendo así la cadena, donde *A = 10*, *B =*  
*11 ...* *Z = 35*.
- (Paso 4) Interperetala cadena como un entero decimal y calcula el residuo de ese número dividiéndolo  
entre 97. Si el residuo es *1*, pasa la prueba de verificación de dígitos y el IBAN puede ser válido.  
  
Observa el código en el editor.  
```
1 |    # Validador IBAN.
2 |
3 |    iban = input("Ingresa un IBAN, por favor: ")
4 |    iban = iban.replace(' ','')
5 |
6 |    if not iban.isalnum():
7 |        print("Has introducido caracteres no válidos.")
8 |    elif len(iban) < 15:
9 |        print("El IBAN ingresado es demasiado corto.")
10|    elif len(iban) > 31:
11|        print("El IBAN ingresado es demasiado largo.")
12|    else:
13|        iban = (iban[4:] + iban[0:4]).upper()
14|        iban2 = ''
15|        for ch in iban:
16|            if ch.isdigit():
17|                iban2 += ch
18|            else:
19|                iban2 += str(10 + ord(ch) - ord('A'))
20|        iban = int(iban2)
21|        if iban % 97 == 1:
22|            print("El IBAN ingresado es válido.")
23|        else:
24|            print("El IBAN ingresado no es válido.")
```  
  
Analicémoslo:  

Observa el código en el editor. Analicémoslo:

- Línea 03: pide al usuario que ingrese el IBAN (el número puede contener espacios, ya que mejoran significativamente la legibilidad del número...
- Línea 04: ... pero remueve los espacios de inmediato).
- Línea 06: el IBAN ingresado debe constar solo de dígitos y letras, de lo contrario...
- Línea 07: ... muestra un mensaje.
- Línea 08: el IBAN no debe tener menos de 15 caracteres (esta es la variante más corta, utilizada en Noruega).
- Línea 09: si es más corto, se informa al usuario.
- Línea 10: además, el IBAN no puede tener más de 31 caracteres (esta es la variante más larga, utilizada en Malta).
- Línea 11: si es más largo, se le informa al usuario.
- Línea 12: se comienza con el procesamiento.
- Línea 13: se mueven los cuatro caracteres iniciales al final del número y se convierten todas las letras a mayúsculas (paso 02 del algoritmo).
- Línea 14: esta es la variable utilizada para completar el número, creada al reemplazar las letras con dígitos (de acuerdo con el paso 03 del algoritmo).
- Línea 15: iterar a través del IBAN.
- Línea 16: si el carácter es un dígito...
- Línea 17: ... se copia.
- Línea 18: de lo contrario...
- Línea 19: ... conviértelo en dos dígitos (observa cómo se hace aquí).
- Línea 20: la forma convertida del IBAN está lista: ahora se convierte en un número entero.
- Línea 21: ¿el residuo de la división de ```iban2``` entre ```97``` es igual a ```1```?
- Línea 22: si es así, entonces el número es correcto.
- Línea 23: de lo contrario...
- Línea 24: ... el número no es válido.  

Agreguemos algunos datos de prueba (todos estos números son válidos; puedes  
invalidarlos cambiando cualquier carácter).  
  
- Inglés: ```GB72 HBZU 7006 7212 1253 00```
- Francés: ```FR76 30003 03620 00020216907 50```
- Alemán: ```DE02100100100152517108```  

Si eres residente de la UE, puedes usar tu propio número de cuenta para hacer pruebas.  


## **Puntos Claves**  

1. Las cadenas son herramientas clave en el procesamiento de datos modernos, ya que la mayoría de los  
datos útiles son en realidad cadenas. Por ejemplo, el uso de un motor de búsqueda web (que parece  
bastante trivial en estos días) utiliza un procesamiento de cadenas extremadamene complejo, que  
involucra cantidades inimaginables de datos.  
  
2. El comparar cadenas de forma estricta (como lo hace Python) puede ser muy insatisfactorio cuando se  
trata de búsquedas avanzadas (por ejemplo, durante consultas extensas a bases de datos). En respuesta  
a esta demanda, se han creado e implementado una serie de algoritmos de comparación de cadenas  
*difusos*. Estos algoritmos pueden encontrar cadenas que no son iguales en el sentido de Python, pero  
que son **similares**.  
Uno de esos conceptos es la **Distancia Hamming**, que se utiliza para determinar la similitud de dos  
cadenas. Si este tema te interesa, pudes encontrar más información aquí:  
[https://en.wikipedia.org/wiki/Hamming_distance](https://en.wikipedia.org/wiki/Hamming_distance)  
Otra solución del mismo tipo, pero basada en un supuesto diferente, es la **Distancia Levenshtein**  
descrita aquí:  
[https://en.wikipedia.org//wiki/Levenshtein_distance](https://en.wikipedia.org//wiki/Levenshtein_distance)  
  

3. Otra forma de comparar cadenas es encontrar su similitud *acústica*, lo que significa un proceso que  
lleva a determinar si dos cadenas suenan similares (como "echo" y "hecho"). Esa similitud debe  
establacerse para cada idioma (o incluso dialecto) por separado.  
Un algoritmo utilizado para realizar una comparación de este tipo para el idioma inglés se llama **Soundex**  
y se inventó, no lo creerás, en 1918. Puedes encontrar más información a respecto aquí:  
[https://en.wikipedia.org/wiki/Soundex](https://en.wikipedia.org/wiki/Soundex)  
  

4. Debido a la precisión limitada de los datos enteros y flotantes nativos, a veces es razonable almacenar  
y procesar valores numéricos enormes como cadenas. Esta es la técnica que usa Python cuando se le  
fuerza a operar con un número entero que consta de una gran cantidad de dígitos.