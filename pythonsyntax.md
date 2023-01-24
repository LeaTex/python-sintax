Sintaxis básica de Python v3.8 y posteriores
===

Referencias:

- <https://docs.python.org/3/index.html>
- <https://docs.python.org/3/tutorial/>
- <https://pymotw.com/3/>
- [The Python Standard Library](https://docs.python.org/3/library/index.html)
- [Guía de estilos](https://www.python.org/dev/peps/pep-0008/)
- [Cheatsheet](https://www.codecademy.com/learn/learn-python-3/modules/learn-python3-hello-world/cheatsheet)
- [Comprehensive Python Cheatsheet](https://gto76.github.io/python-cheatsheet/)
- [Programación funcional](https://docs.python.org/3.7/howto/functional.html)
- [Tips](https://testdriven.io/tips/)

---
# Tipos básicos

## Números

Suma: `45 + 94` --> `139`

Resta: `94 - 45` --> `49`

Multiplicación: `94 * 88` --> `8272`

División decimal: `94 / 45` --> `2.0888888889`

Cociente (División entera - DIV): `94 // 45` --> `2`

Resto (MOD): `94 % 45` --> `4`

Cociente y resto: `divmod(94,45)` --> `(2, 4)`  
retorna tupla (cociente, resto): `(94 // 45, 94 % 45)`

Potencia: `3 ** 5` --> `243`  
o también: `pow(3, 5)`--> `243`

Valor absoluto (módulo): `abs(-45)` --> `45`

Se pueden convertir números o cadenas que representen números.
Convertir a int: `int(strNumber)`  
Convertir a float: `float(aNumber)`  
Convertir a string: `str(aNumber)`

Tipos:  
enteros: `1243`  
decimales de punto flotante: `457.54` o `7883.0` o `4785.`  
notación científica: `4.445e8` es decir: `4.445 * 10 ** 8` (el exponente puede ser negativo)  
complejos: `2+3j` o `5-3i`

Número mínimo y máximo definidos como flotantes: `-1e308` y `1e308`

### Constantes en el módulo math

Pi: `math.pi`  
Tau: `math.tau`  
Euler: `math.e`  
Infinito: `math.inf` o `float('inf')`  
NaN (Not a Number): `math.nan` o `float('NaN')`

TODO: raíces <https://youtu.be/XZ5yDv5Iz5I>  
TODO: módulo math <https://youtu.be/TBc29BdhgE0>  
TODO: integers & floats <https://youtu.be/Nc1BhYKs56Y>

## Cadenas

Cadena simple: `'Una cadena cualquiera'`  
o también: `"Una cadena cualquiera"`

Incluyendo comillas: `'Una cadena con "comillas dobles"'`  
o también: `"Una cadena con 'comillas simples'"`

Escapando comillas: `'Una cadena con \'comillas simples\''`

Con saltos de línea:

```python
'''Una cadena cualquiera que incluye 
salto de línea se hace con triple 
comillas (simples o dobles)'''
```

O usando `\n` en medio de la cadena: `'Acá va un salto de línea\ny luego sigue'`

Concatenando con `+`: `'Una cadena ' + 'otra cadena'`

Concatenando con comodines: `'Una cadena %s y otra %s' %('CadenaUno', 'CadenaDos')`  
Se puede usar `%d` para enteros y `%f` para reales, entre otros.  

Esos especificadores permiten formatear, por ejemplo:  
`%5s` completa hasta 5 espacios a izquierda  
`%-5s` completa hasta 5 espacios a derecha  
`%.7s` incluye hasta 7 caracteres de la cadena  
Y también se pueden utilizar para formatear números.

Concatenando con interpolación usando *placeholders* genéricos: `'Una cadena {} y otra {}'.format('CadenaUno', 'CadenaDos')`  
o de variables: `'Una cadena {str1} y otra {str2}'.format(str1 = 'CadenaUno', str2 = 'CadenaDos')`

Se puede usar una cadena preformateada (FString) con variables ya definidas:  
`f'Una cadena con variable {una_variable} y otra {otra_variable}'`  
Si se coloca un = luego del nombre de la variable se imprime mostrando la misma junto al valor:  
`f'Una cadena con {una_variable=} y {otra_variable=}'`  
Y también se pueden evaluar expresiones: `f'El resultado es {1 + 2}'`

Repetir cadenas: `'una cadena' * 5`

Todo en mayúsculas: `unaCadena.upper()`  
Preguntar si está en mayúsculas: `unaCadena.isupper()`

Todo en minúsculas: `unaCadena.lower()`  
Preguntar si está en minúsculas: `unaCadena.islower()`

Camel case (tipo título): `unaCadena.title()`

Primera en mayúscula: `unaCadena.capitalize()`

Cambiar mayúsculas por minúsculas y viceversa: `unaCadena.swapcase()`

Índice donde inicia una subcadena: `unaCadena.find(subcadena)`  
Empezando la búsqueda a partir de cierta posición: `unaCadena.find(subcadena, posicion)`  
Índice donde inicia una subcadena, buscando hacia atrás: `unaCadena.rfind(subcadena)`

Cantidad de veces que aparece una subcadena: `unaCadena.count(subcadena)`

Detectar una letra en la cadena: `unaLetra in unaCadena`  
Detectar una subcadena: `subcadena in unaCadena`

Detectar cómo inicia una cadena: `unaCadena.startswith(otraCadena)`  
Detectar cómo finaliza una cadena: `unaCadena.endswith(otraCadena)`

Indica si es un número: `una_cadena.isdigit()`  
Indica si contiene sólo caracteres alfatéticos: `una_cadena.isalpha()`  
Indica si contiene sólo caracteres alfanuméricos: `una_cadena.isalnum()`

Dividir en subcadenas (split) usando espacios: `unaCadena.split()`  
Dividir en subcadenas según una subcadena: `unaCadena.split(subcadena)`  
Dividir en subcadenas por líneas: `unaCadena.splitlines()`

Juntar cadenas de una lista usando un separador: `separador.join(unaListaDeCadenas)`  
Ej.: `';'.join(['Carlos','Gomez','30444555'])` --> `'Carlos;Gomez;30444555'`

Reemplazar una subcadena por otra: `unaCadena.replace(subcadena, reemplazo)`  
Reemplazar una subcadena por otra N veces: `unaCadena.replace(subcadena, reemplazo, veces)`

Longitud: `len(unaCadena)`

Sacar espacios y enters
a izquierda: `unaCadena.lstrip()`
a derecha: `unaCadena.rstrip()`
a ambos lados: `unaCadena.strip()`

Una cadena se puede manipular como lista, accediendo a sus componentes por el índice: `unaLetra = unaCadena[i]`

O subcadenas: `subcadena = unaCadena[0:3]`  
`principio = unaCadena[:3]`  
`final = unaCadena[4:]`  
`completa = unaCadena[:]`

Alinear a completando con espacios hasta N:  
a izquierda: `una_cadena.ljust(50)` completa a derecha  
a derecha: `una_cadena.rjust(50)` completa a izquierda  
centrado: `una_cadena.center(50)` completa a ambos lados

También se puede reemplazar el espacio por algún caracter:  
a izquierda: `una_cadena.ljust(50, '-')`
a derecha: `una_cadena.rjust(50, '*')`
centrado: `una_cadena.center(50, '+')`


TODO: format https://youtu.be/RIpPmdCgR8c y https://youtu.be/3r1Sq4RYnvg

## Listas

El índice inicia en 0 (el primer elemento).

Constructor: `[]` o llamando a la función `list()`.

Lista: `['a', 'b', 'c', 'd', 'e', 'f', 'g']`

Agregar elemento al final: `unaLista.append(unElemento)`

Insertar elemento en alguna posición: `unaLista.insert(indice, unElemento)`

Remover elemento: `unaLista.remove(unElemento)`  
Sólo remueve la primer aparición del elemento en la lista.

Remover elemento por su índice: `del(unaLista[indice])` o `del unaLista[indice]`

Remover el último y retornarlo (modo pila): `unaLista.pop()`

Remover todos los elementos (vaciar la lista): `unaLista.clear()`

Devolver elemento de alguna posición: `unaLista[indice]`  
El índice puede ser negativo (lista circular): `unaLista[-1]`

Setear o cambiar un elemento de la lista: `unaLista[indice] = unObjeto`

Concatenar listas: `unaLista.extend(otraLista)`  
Agrega todos los elementos de `otraLista` a `unaLista`, o sea se modifica la lista receptora.  
Hacer `unaLista.append(unElemento)` es lo mismo que `unaLista.extend([unElemento])`

Concatenar listas: `unaLista + otraLista`  
Devuelve un nuevo objeto lista con ambas listas encadenadas.

Repetir lista: `unaLista * un_entero`

Cantidad de elementos de una lista: `len(unaLista)`  
Si la cantidad es N, el último elemento está en la posición N-1.

`unaLista[len(unaLista)]` --> Out of range  
`unaLista[len(unaLista)-1]` --> último elemento  
`unaLista[-1]` --> último elemento

Devolver sublista: `unaLista[indiceInicio : indiceFin]`  
El elemento de `indiceFin` no se incluye en la sublista.

Devolver sublista salteando elementos: `unaLista[indiceInicio : indiceFin : salto]`

Devolver sublista salteando y recorriendo toda (no se ponen índices): `unaLista[::salto]`

Devolver lista invertida: `unaLista[::-1]`  
Con un salto negativo se recorre en sentido inverso.

### Operaciones comunes

Ordenar lista en forma ascendente (si sus elementos son comparables y ordenables): `unaLista.sort()`

Ordenar lista en forma descendente: `unaLista.sort(reverse = True)`

Devolver una nueva lista con orden invertido: `reversed(unaLista))`

También se puede llamar a la función: `sorted(unaLista, reverse = True)`  
Retorna una nueva lista, sin modificar la original.

Buscar el menor valor: `min(unaLista)`

Buscar el mayor valor: `max(unaLista)`

Buscar elemento en una lista  
existencia: `elemento in unaLista`  
ausencia: `elemento not in unaLista`

Índice de un elemento en una lista: `unaLista.index(elemento)`

Cantidad de veces que aparece un elemento en una lista: `unaLista.count(elemento)`

### Lista comprimida (List comprehension)

Crea una lista a partir de un objeto iterable (como una lista):
`[ nuevoElemento for unElemento in objetoIterable ]`

Se pueden poner condicionales simples al final:
`[ nuevoElemento for unElemento in objetoIterable if condicionBooleana ]`

O condicionales compuestos al inicio:
`[ nuevoElemento if condicionBooleana else otroElemento for unElemento in objetoIterable ]`

## Tuplas

Constructor: `tuple()`  
A partir de varios elementos: `(unElemento, otroElemento)`

Se pueden crear concatenando objetos con una coma: `unaTupla = unaVariable , 'cadena', 123 , True`

Es como una lista, puede tener N elementos, pero la tupla es inmutable.  
Tienen casi todo el mismo protocolo que las listas, incluyendo el protocolo de `:` para obtener subtuplas usando los índices.  
Se utilizan como un registro (record).  
Se puede conocer su tamaño (la cantidad de elementos que tiene), y acceder a ellos por índices.  
Son comparables, y por lo tanto ordenables.

Recorrer una tupla:

```python
for elem1, elem2, elemN in unaListaDeTuplas:
    pass
```

Desempaquetado de tuplas usando asignación múltiple: `(x, y, z) = ('elemento 1', 'elem 2', 'elem 3')`  
Se pueden omitir los paréntesis: `x, y, z = 'elemento 1', 'elem 2', 'elem 3'`

### TODO: Listas

- agregar comprimir (compactar, empaquetar) y descomprimir (desempaquetar), uso de cabeza y cola, _ y *
ej: *(1, 2, 3)  --> 1  2  3
https://codigofacilito.com/videos/desempaquetado
https://youtu.be/YPKFbxtJ2s0


## Conjuntos

Constructor: `set()`  
O a partir de una lista: `unConjunto = set(unaLista)`  
O con sus elementos: `{elemento1, elemento2, elemento3}`

Un conjunto no tiene duplicados.
Un conjunto no está ordenado.

Agregar elemento al final: `unConjunto.add(unElemento)`

Remover un elemento (al azar) y retornarlo: `unConjunto.pop()`

Intersección de conjuntos: `unConjunto & otroConjunto`  
o también: `unConjunto.intersection(otroConjunto)`

Unión de conjuntos: `unConjunto.union(otroConjunto)`

Diferencia de conjuntos: `unConjunto.difference(otroConjunto)`

Determinar si un conjunto es subconjunto de otro: `unSubconjunto.issubset(unConjunto)`

Determinar si un conjunto contiene a otro: `unConjunto.issuperset(unSubconjunto)`

### Conjunto comprimido (Set comprehension)

Se crea igual que la lista copmrimida, pero usando `{}` en lugar de `[]`:
`{ nuevoElemento for unElemento in objetoIterable }`

## Diccionarios

Constructor: `{}` o llamando a la función `dict()`.  
El manejo es parecido a una lista.

Diccionario: `{clave : valor, 'a' : 1, 34: 'cadena'}`

Agregar un elemento: `unDiccionario[clave] = valor`

Eliminar una clave con su elemento: `del unDiccionario[clave]`

Buscar una clave en el diccionario:  
existencia: `aKey in unDiccionario`  
ausencia: `aKey not in unDiccionario`

Obtener un elemento: `unDiccionario[clave]`

Obtener un elemento pero si la clave no existe devolver None: `unDiccionario.get(clave)`  
Obtener un elemento pero si la clave no existe devolver un default: `unDiccionario.get(clave, default)`  
Obtener un elemento pero si la clave no existe agregarla: `unDiccionario.setdefault(clave, default)`

Remover una clave y retornar su valor: `unDiccionario.pop(unaClave)`

Remover todos los elementos (vaciar el diccionario): `unDiccionario.clear()`

Obtener las claves: `unDiccionario.keys()` devuelve un objeto dict_keys.  
También se puede devolver una lista: `list(unDiccionario)` o `list(unDiccionario.keys())`  
O una tupla: `tuple(unDiccionario)` o `tuple(unDiccionario.keys())`

Obtener los valores: `unDiccionario.values()` devuelve un objeto dict_values.  
También se puede convertir con `list()` o `tuple()`.

Obtener las tuplas `(clave, valor)` en un objeto dict_items: `unDiccionario.items()`  
Que se puede convertir con `list()` o `tuple()`.

Recorrer un diccionario por claves: `for aKey in unDiccionario: pass`  
Sería lo mismo que hacer: `for aKey in unDiccionario.keys(): pass`

Recorrer un diccionario clave y valor: `for aKey, aValue in unDiccionario.items(): pass`  
Esto es gracias a las tuplas, no es propio de los diccionarios.

Cantidad de elementos: `len(unDiccionario)`

Devolver un nuevo diccionario con orden invertido: `reversed(unDiccionario))`

Nuevo diccionario a partir de otros: `nuevoDic = {**unDic, **otroDic}`  
Desde Python 3.9 existe el `|`: `nuevoDic = unDic | otroDic`

Actualizar diccionario a partir de otro: `unDic.update(otroDic)`  
Desde Python 3.9 existe el `|=`: `unDic |= otroDic`

### Diccionario comprimido (Dict comprehension)

Crea un diccionario a partir de tuplas o lista:  
`{ unaClave : unValor for unaClave, unValor in unaListaDeTuplas }`  
`{ unaClave : unValor for unElemento in unaLista }`

Se pueden poner condicionales simples al final:
`{ unaClave : unValor for unElemento in unaLista if condicionBooleana }`

## Nulo

Valor nulo, null o nil: `None`  
Es reconocido como falso en una expresión booleana.

## Booleanos

Verdadero: `True`  
Falso: `False`

Otros valores reconocidos como `False` son:

- `None`
- valores 0 y 0.0
- `""` string vacío
- `[]` lista vacía
- `()` tupla vacía
- `{}` diccionario vacío

Todos los demás objetos que no sean esos serán reconocidos como `True`.

Se pueden invertir con la función: `not(aBool)`  
O en formato: `not aBool`

Se pueden castear booleanos a enteros y viceversa:  
`bool(1)` --> `True`  
`bool(0)` --> `False`  
`int(True)` --> `1`  
`int(False)` --> `0`

___

# Operadores

Más:  
- <https://www.instagram.com/p/Ch_Txtirbu9/>  
- <https://www.w3schools.com/python/python_operators.asp>  
- <https://docs.python.org/3/library/operator.html>  
- <https://www.freecodecamp.org/espanol/news/operadores-basicos-en-python-con-ejemplos/>

## Operadores de asignación

Asignación simple: `una_variable = unValor`

Asignación múltiple (tipo tupla): `una_variable, otra_variable = unValor, otroValor`  
Es útil para para hacer un "swap" de valores, sin recurrir a una variable temporal: `var1, var2 = var2, var1`

Sumar y asignar: `una_variable += unValor`

Restar y asignar: `una_variable -= unValor`

Multiplicar y asignar: `una_variable *= unValor`

Dividir y asignar: `una_variable /= unValor`

Módulo y asignar: `una_variable %= unValor`

División entera y asignar: `una_variable //= unValor`

Potencia y asignar: `una_variable **= unValor`

Actualizar diccionario y asignar (desde Python 3.9): `un_dic |= otro_dic`

Asignar y evaluar (walrus): `:=`

## Operadores relacionales

`<` Menor  
`<=` Menor o igual  
`==` Igual  
`>=` Mayor o igual  
`>` Mayor  
`!=` Distinto

#### Comparador is
Mientras el operador `==` compara por igualdad de valores, la función `is` compara por identidad, es decir, por espacios de memoria.  
Si `un_objeto is otro_objeto` entonces `id(un_objeto) == id(otro_objeto)`.  
Si `un_objeto == otro_objeto` no necesariamente `un_objeto is otro_objeto`.

## Operadores lógicos

Conjunción: `unBooleano and otroBooleano`

Disjunción: `unBooleano or otroBooleano`

Negación: `not unBooleano`

El operador `or` se puede utilizar para asignar a una variable el primer valor que sea verdadero: `variable = valor_booleano or otro_booleando or otra_expresion_booleana`

## Operadores binarios

TODO: https://www.journaldev.com/14082/python-operators

___

# Control de flujo - Ciclos

## Condicional IF

```python
if (condición booleana):
    pass
```

En una línea: `if (condición booleana): pass`

```python
if (condición booleana):
    pass
else:
    pass
```

```python
if (condición booleana):
    pass
elif (condición booleana):
    pass
else:
    pass
```

Circuito invertido (operador ternario), se usa para asignación:  
`unaVariable = unValor if (condición booleana) else otroValor`

## Condicional MATCH-CASE

A partir de la versión 3.10 se puede utilizar el `match` que es similar el `switch` en otros leguajes.  

```python
match objeto_a_comparar:
    case un_valor:
        pass
    case otro_valor:
        pass
    case _:
        pass
```

Se puede utilizar para _matchear_ con un patrón (se hace _pattern matching_), por ejemplo, un diccionario con ciertas claves:

```python
un_objeto = {'nombre': una_cadena, 'edad': un_numero}

match un_objeto:
    case {'nombre': nombre, 'edad': edad}:
        pass
    case {'cantidad': cantidad, 'precio': precio}:
        pass
    case _:
        pass
```

También se puede comparar contra un conjunto de valores usando el operador de unión `|`:

```python
match objeto_a_comparar:
    case un_valor | otro_valor | un_valor_distinto :
        pass
    case nuevo_valor | otro_nuevo_valor:
        pass
    case _:
        pass
```

Se pueden comprar listas por cantidad de elementos:

```python
match una_lista:
    case [valor] :
        pass
    case [valor, otro_valor]:
        pass
    case [valor, *mas_valores]:  #cantidad indeterminada de elementos
        pass
    case _:
        pass
```

Y combinar condiciones con estas propiedades:

```python
match una_lista:
    case [valor_buscado , segundo_elemento] :
        pass
    case [(un_valor | otro_valor) , segundo_elemento] :
        pass
    case [(nuevo_valor | distinto_valor) , segundo_elemento] if segundo_elemento in [buscado, otro_buscado]:
        pass
    case _:
        pass
```


## Ciclo WHILE

```python
while (condición booleana verdadera):
    pass
```

`break` termina la ejecución de un bloque de código

```python
while (condición booleana verdadera):
    break
```

`continue` avanza al próximo ciclo

```python
while (condición booleana verdadera):
    if condition:
        pass
    elif conditionTwo:
        continue
    else:
        break
```

Se puede agregar un bloque `else` que se ejecuta cuando la condición no es verdadera, pero no se ejecuta si el ciclo termina con un `break` o `return`.  
```python
while (condición booleana verdadera):
    pass
else:
    pass
```

## Ciclo FOR

Recorre una colección ordenada de principio a fin. No tienen que ser necesariamente números.

```python
for object in objeto_iterable:
    pass
```

```python
for i in range(5):
    pass
```

```python
for i in [5, 4, 3, 2, 1]:
    pass
```

```python
for aName in ['Juan', 'Pedro', 'Carlos']:
    pass
```

Se puede agregar un bloque `else` que se ejecuta cuando el bucle terminó por completo, pero no se ejecuta si el ciclo termina con un `break` o `return`.  
```python
for object in objeto_iterable:
    pass
else:
    pass
```

## Saltos y cortes en los ciclos (break y continue)

Se pueden utilizar en `for` o `while`.

`break` corta la ejecución del ciclo por completo y continúa la ejecución con la siguiente sentencia fuera del ciclo.

`continue` corta la ejecución del ciclo actual y continúa con el ciclo siguiente, es decir, "saltea" todo lo que resta ejecutar del ciclo y avanza en la ejecución.

___

# Otras

## Manejo de excepciones

```python
try:
    # si ocurre un error, se ejecutará el código de except
    pass
except OneException as exceptionVariable:
    pass
except OtherException, AnotherException as exceptionVariable:
    pass
except:  # except Exception as e:
    # manejo de excepciones no esperadas
    pass
else:
    # se evalúa si no hubo excepciones
    pass
finally:
    # se evalúa siempre, aunque hubiera alguna excepción previa
    pass
```

Levantar una excepción: `raise MyError`  
Con descripción: `raise MyError("Error description")`

TODO: revisar el video https://youtu.be/YMx645JNBxk  
TODO: revisar excepciones conocidas  (value error, key error, type error, name error, etc)  
TODO: crear excepción personalizada

## Comentarios

`# comentario de una línea`

```python
"""
comentario en párrafo se hace con 3 comillas dobles
como se muestra en este ejemplo
"""
```

## Imprimir por consola

TODO: print() completar, revisar parámetro sep, uso de __repr__()

## Constantes

Por convención se definen en mayúsculas fuera de las funciones y clases: `UNA_CONSTANTE = un_valor`

## Lectura por teclado

Se utiliza la función `input()`

Se puede acompañar con texto: `input("Ingrese su nombre: ")`

Todos las valores leídos son texto, por lo que habrá que hacer conversiones de tipos en caso de ser necesario.

### TODO: teclado
- función eval()

## Palabras reservadas

```python
and as assert break class continue def del elif else except 
False finally for from global if import in is lambda None 
nonlocal not or pass reise return True try while with yield
```

Se pueden ver desde Python directamente:
```python
import keyword
keyword.kwlist
```

___

## Archivos

Abrir un archivo: `file_handler = open(fileName)`
Indicando el modo: `file_handler = open(fileName, mode)`

Leer desde la posición del puntero hasta el final: `contents = file_handler.read()`

Leer una determinada cantidad de bytes: `contents = file_handler.read(cantidad)`  
Deja el puntero en la última posición leída y se puede continuar a partir de ahí.

Leer una línea: `line = file_handler.readline()`  
Leer todas las líneas: `lines = file_handler.readlines()`

Recorrer por líneas:

```python
for line in file_handler:
    pass
```

Ubicar el puntero en una posición: `file_handler.seek(posicion)`

Escribir una línea: `file_handler.write("Una línea de texto")`  
Escribir varias líneas: `file_handler.writelines(lista_de_lineas)`

Cerrar el archivo: `file_handler.close()`

Indica si está cerrado: `file_handler.closed`

Cierra automáticamente el archivo luego de usarlo:

```python
with open(file_name) as file_handler:
    pass
```

Se puede utilizar para más de un archivo:

```python
with open(file_name) as file_handler, open(other_name) as other_handler:
    pass
```

O también:

```python
with (open(file_name) as file_handler, 
      open(other_name) as other_handler):
    pass
```

Modos:  
`r` read only  
`rb` read binary  
`r+` read and write  
`w` write  
`wb` write brinary  
`a` append  
`ab` append binary

TODO: context manager <https://youtu.be/J5paZNIqqHI> , <https://youtu.be/qkpURBYk7Eo>