# Funciones

Más: <https://docs.python.org/3/library/functions.html>

## Generalidades

Pueden no tener argumentos, y no tener retorno.  
El valor de retorno por defecto es `None`.

```python
def nombre_funcion(argumento):
    variable_local = unValorDeterminado
    pass
    return aValue
```

Argumentos con valores default (se pueden omitir al momento de invocarse):

```python
def nombre_funcion(argumento = unValorDefault):
    pass
```

Si en la invocación se utiliza el nombre de cada parámetro, se puede alterar el orden de los mismos.  
Orden por defecto (por posición): `nombre_funcion(valor1, valor2, valor3)`  
Orden modificado (por nombre): `nombre_funcion(argumento2=valor2, argumento3=valor3, argumento1=valor1)`

Las funciones pueden ser asignadas a variables, utilizadas como argumentos, o retornarse como resultado de otra función. Esto es porque son "ciudadanos de primer orden".

### Usos especiales de parámetros

Lista de parámetros en formato tupla o lista. Se puede utilizar el argumento como cualquier tupla o lista, iterándola o accediendo por índice. Permite pasar una cantidad variable de argumentos posicionales:

```python
def nombre_funcion(*args):
    for arg in args:
        pass

nombre_funcion(unArgumento, otroArgumento, unNuevoArgumento)

args = (unArgumento, otroArgumento, unNuevoArgumento)
nombre_funcion(*args)
```

Lista de parámetros en formato diccionario. Se puede utilizar el diccionario argumento como cualquier diccionario, generalmente accediendo por clave. Permite pasar una cantidad variable de argumentos por nombre:

```python
def nombre_funcion(**kwargs):
    kwargs[unaClave]
    kwargs[otraClave]
    for key, value in kwargs.items():
        pass

nombre_funcion(unaClave = unArgumento, otraClave = otroArgumento)

kwargs = {'unaClave' : unArgumento, 'otraClave' : otroArgumento}
nombre_funcion(**kwargs)
```

Se puede utilizar el argumento especial `/` para separar, a su izquierda, argumentos exclusivamente posicionales, y a su derecha, argumentos de cualquier tipo (posicionales o de palabras).  
```python
def nombre_funcion(arg_pos1, arg_pos2, /, arg3, arg4, arg5):
    pass

nombre_funcion(unArgumento, otroArgumento, unValor, arg5=otroValor, arg4=nuevoValor)
```

### Scope (alcance) de variables

Las variables definidas en distintos contextos pueden tener el mismo nombre.  
Las variables globales tienen alcance global. Solo se puede modificar su valor en el bloque de código donde fue creada, pero puede leerse en cualquier lado.  
Las variables locales solo se utilizan en el bloque de código donde se creó, o algún bloque interno.  
Al momento de usarse una variable, primero se chequea el alcance local, y si no se encuentra se busca la variable en el alcance superior.

```python
variable_global = un_valor

def nombre_funcion():
    # variable local con el mismo nombre
    variable_global = None
    variable_local = None
```

Para modificar el valor de una variablo global se puede indicar que se va a usar una variable de otro contexto:  
```python
variable = un_valor

def nombre_funcion():
    global variable
    variable = otro_valor
```

TODO: - uso de nonlocal para variables dentro de funciones anidadas https://www.programiz.com/python-programming/global-local-nonlocal-variables

### Documentación (docstring y doctest):

```python
def nombre_funcion(argumento=unValorDefault):
    """Summary or Description of the Function

    Parameters:
    argument1 (int): Description of arg1

    Returns:
    int: Returning value
    """
    pass
```

La documentación puede ser accedida por el atributo `doc`: `nombre_funcion.__doc__`  
O usando la función: `help(nombre_funcion)`

También se puede agregar docstring en los módulos, y objetos. En todos los casos se puede acceder con la función:  
`help(modulo)`  
`help(UnaClase)`  
`help(UnaClase.un_metodo)`  
`help(un_metodo)`

El módulo `doctest` permite hacer pruebas rápidas de las funciones, si dentro de su documentación se encuentran invocaciones a modo de ejemplo como si se ejecutaran desde el shell.

```python
def nombre_funcion(argumento=unValorDefault):
    """
    Lo que sigue es para doctesting

    >>> nombre_funcion(123)
    resultadoEsperado

    >>> nombre_funcion('abc')
    resultadoEsperado
    """
    pass
```

Se ejecutan las pruebas llamando al módulo:  
`python -m doctest miarchivo.py`

También se puede testear el módulo a sí mismo al ejecutarlo directamente:  
```python
def nombre_funcion(argumento=unValorDefault):
    """
    Lo que sigue es para doctesting

    >>> nombre_funcion(123)
    resultadoEsperado
    """
    pass

import doctest
doctest.testmod()
```

### Alias de funciones

Se asigna el nombre de la función a una variable, que se puede usar como la función original:  

```python
def nombre_funcion(argumento=unValorDefault):
    pass

variableFuncion = nombre_funcion

nombre_funcion(valor)
variableFuncion(valor)
```

## Funciones anidadas
TODO: completar

## Generadores

Retornan un objeto *lazy iteration* que permite ser iterado, pero sin que esté en memoria toda la colección a iterar.
Se utiliza `yield` en lugar de `return`.

```python
def funcion_generador():
    for e in objeto_iterable:
        yield e

for elem in funcion_generador():
    print(elem)
```

`next()` permite solicitar al generador el siguiente elemento.  
Si llega al final de la iteración se dispara una excepción `StopIteration` por lo que conviene hacer algo al respecto.

```python
generador = funcion_generador()
while True:
    try:
        print(next(generador))
    except StopIteration:
        break
```

También se puede instanciar como una expresión "comprimida":  
`generador = (elem for elem in objeto_iterable)`

`send()` permite pasarle un parámetro a `yield` para alterar la ejecución, haciendo que el próximo elemento a generar y retornar dependa de ese dato.

```python
def funcion_generador():
    numero = 0
    while True:
        numero = yield numero + 1

generador = funcion_generador()
print(generador.send(120))
```

Una vez utilizada `send()` no conviene utilizar `next()` sobre el generador, porque esta asigna `None` al valor, provocando que se genere un `StopIteration`.

`throw()` le indica al generador que lance una excepción, y de ese modo finaliza su iteración.  
Una vez disparada la excepción el generador retorna `StopIteration` si vuelve a invocarse.  
`generador.throw(ValueError('un mensaje descriptivo'))`

`close()` le indica al generador que finaliza su iteración, pero sin provocar una excepción específica.  
Una vez finalizado genera un `StopIteration` si vuelve a invocarse.  
`generador.close()`

Más: <https://docs.python.org/3.7/howto/functional.html#generator-expressions-and-list-comprehensions>

TODO: yield from

## Rangos

Constructor: `range()`  
Va generando una secuencia (rango) de números según las condiciones dadas por parámetro.  
El funcionamiento es similar a un generador, pero no tiene el mismo protocolo.

Rango de 0 a N sin incluir: `range(15)`  
Por defecto inicia en 0.

Rango de N (incluido) a M (sin incluir): `range(3, 20)`

Rango de N a M con salto cada D: `range(1, 10, 2)`  
Por defecto el salto es 1.

Rango decreciente de N a M (con N > M): `range(50, 10, -1)`

## Enumeraciones

Constructor: `enumerate()`
Agrega índices a un objeto iterable, retornando tuplas donde el primer elemento es el índice, y el segundo el objeto de la lista original.  
El funcionamiento es similar a un generador, pero no tiene el el mismo protocolo.  
`lista_indexada = enumerate(una_lista)`

```python
for indice, elemento in enumerate(una_lista):
    pass
```

## Expresiones Lambda

Funciones anónimas o expresiones lambda (ideales para expresiones sencillas).  
No llevan nombre, y se escriben en una sola línea.  
El retorno es la evaluación de la expresión:  
`variable_funcion = lambda arg : expresión`  
`variable_funcion = lambda arg1, argN : expresión`

Los parámetros tienen las mismas condiciones de los parámetros de cualquier función. Pueden ser posicionales o por nombre, obligatorios u opcionales (con valores default), y tener una cantidad variable.  
`variable_funcion = lambda arg1, arg2=valor, *args, **kwargs : expresión`

Se invocan como una función normal:  
`variable_funcion(valor_argumento)`


## Callbacks (funciones como parámetros)

Son funciones (o lambdas) que se pasan como parámetro a otra función.

```python
mi_callback = lambda arg : expresión

def nueva_funcion(func_callback, arg2):
    func_callback(arg2)

nueva_funcion(mi_callback, un_valor)
```


## Clousures (funciones que retornan función)

Un clousure es una función que retorna otra función, la cual puede acceder a las variables de la función principal por más que haya finalizado su ejecución.

```python
def funcion_clousure(argumento):
    variable_local = argumento
    
    def funcion_anidada():
        pass
        return variable_local
    
    return funcion_anidada

otra_fx = funcion_clousure(unValor)
otra_fx()
```

## Decoradores

Una función decoradora recibe como argumento una función a decorar, y devuelve otra función decorada.  
Se utilizan para agregar funcionalidad a una función que no se puede/quiere modificar.

```python
def decorador(a_decorar):
    
    def decorada():
        pass
        a_decorar()
        pass
    
    return decorada
```

Para utilizarse el decorador se invoca antes de la definición de la función a decorar:  
```python
@decorador
def funcion_a_decorar():
    pass
```

El invocar la función a decorar, el resultado será el que se obtenga de ejecutar la función decorada. Si la misma no tiene retorno, el resultado será el valor por defecto None.

Se pueden pasar parámetros para que la invocación de la función original no falle:  
```python
def decorador(a_decorar):

    def decorada(*args, **kwargs):
        pass
        return a_decorar(*args, **kwargs)

    return decorada
```


## Funciones sobre objetos iterables

### Función sorted()

Nueva lista ordenada: `lista_ordenada = sorted(lista)`  
Ordenada en forma invertida: `lista_ordenada = sorted(lista, reverse=True)`  
Indicar el criterio (función) para ordenar: `lista_ordenada = sorted(lista, key=func)`  o `lista_ordenada = sorted(lista, key=lambda x: ...)`

### Función map()

`map()` recorre un objeto iterable (lista) y aplica una función para cada elemento de la lista. Retorna un objeto map, que se puede convertir a lista, con los resultados de evaluar la función para cada elemento. (Es como el `collect:` de Smalltalk.)

Se puede usar con funciones: `resultado = map(nombre_funcion, lista)`  
O con expresiones lambda: `resultado = map(lambda elemento : expresión , lista)`

Se puede reemplazar por una lista comprimida:  
`[ funcion(unElemento) for unElemento in lista ]`

También se puede usar si la función recibe N parámetros, con N listas. Se itera para los elementos de la lista más larga, y si no tienen la misma longitud se completan con None (lo cual podría generar errores).  
`map(funcion_tres_parametros, lista_uno, lista_dos, lista_tres)`

### Función filter()

`filter()` recorre un objeto iterable y aplica una función que retorna un valor booleano para cada elemento. Retorna un objeto filter, que se puede convertir a lista, con los elementos de la lista original que devolvieron True al evaluar la función. (Es como el `select:` de Smalltalk.)

Se puede usar con funciones: `resultado = filter(nombre_funcion, lista)`  
O con expresiones lambda: `resultado = filter(lambda elemento : expresión , lista)`

Se puede reemplazar por una lista comprimida condicional:  
`[ unElemento for unElemento in lista if funcionBooleana(elemento) ]`

### Función reduce()

`reduce()` recorre un objeto iterable y aplica una función de 2 parámetros a los elementos, usando el resultado de cada evaluación como primer argumento para la siguiente. Retorna un único valor, resultado de aplicar la función iterativamente sobre todos los elementos. Se debe importar el módulo `functools` para poderla utilizar. (Es como el `inject:into:` de Smalltalk.)

Se puede usar con funciones: `resultado = reduce(nombre_funcion, lista, valorInicial)`  
O con expresiones lambda: `resultado = reduce(lambda resultadoPrevio, unElemento : expresión , lista, valorInicial)`  
El valor inicial es opcional, en ese caso la primera evaluación se hace con los 2 primeros elementos de la lista.

Para utilizarla hay que importar el módulo `functools`.

### Funciones all() any()

`any(unaListaDeBooleanos)` retorna True si alguno de los elementos de la lista es True.

`all(unaListaDeBooleanos)` retorna True si todos los elementos de la lista son True.

Útiles para usar iterables o listas comprimidas.  
Ej: `all(aBooleanExpression for aValue in aList)`

### Funciones zip() zip_longest()

`zip()`retorna un iterador con tuplas de N componentes a partir de aparear N listas. Se utiliza para iteraciones en paralelo.  
La longitud del iterador corresponde a lo longitud de la lista más corta.  
`zipped = zip(unaLista, otraLista)`

Se puede indicar que sea obligatorio que las listas tengan la misma longitud, y en caso contrario se levantará un error:  
`zipped = zip(unaLista, otraLista, strict=True)`

`zip_longest()` funciona igual que `zip()` pero utilizando la longitud de la lista más larga, y armando las tuplas con un valor de "relleno" para la lista más corta. Este valor por defecto es `None` pero se puede cambiar usando el parámetro `fillvalue`.  
`zipped = zip_longest(unaLista, otraLista)`  
`zipped = zip_longest(unaLista, otraLista, fillvalue='Empty')`

Dada una lista de listas, se pueden aparear pasándola como parámetro "empaquetado" con argumentos posicionales:  
`zipped = zip(*listaDeLista)`

También dada una lista de tuplas, se puede "desaparear" en una lista de listas enviándola también como parámetro empaquetado:
`zipped = zip(*listaDeTuplas)`

### TODO: funciones
- reversed()
- parámetros con ++
- annotations (tipos en los parámetros y retornos)
- anotaciones (tipado)
- función assert
- funciones de orden superior
