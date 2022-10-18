# Objetos
- <https://www.python-course.eu/python3_properties.php>
- <https://realpython.com/instance-class-and-static-methods-demystified/>


## Generalidades

Clase de un objeto: `type(anObject)`

Métodos de un objeto: `dir(anObject)`

Detalles de un objeto (muestra el docstring): `help(anObject)`

Definición de una clase:  
```python
class MiClasePadre():
    VARIABLE_DE_CLASE = unValor

    variable_de_clase_dos = otroValor

    def __init__(self, valorNuevo):
        # método constructor
        self.variable_de_instancia = valorNuevo

    def metodo(self):
        pass
```

Se pueden definir atributos y métodos "privados" utilizando doble _ en el nombre, y solo podrán accederse desde la propia instancia.  
```python
class MiClasePadre():
    def __init__(self, valorNuevo):
        self._atributo_protegido = "usa guión bajo"  # es simbólico porque igual se puede acceder
        self.__atributo_privado = None  # se accede con _MiClasePadre__atributo_privado
        self.variable_de_instancia = valorNuevo

    del __metodo_privado(self):
        pass
```

## Atributos 

Se pueden definir atributos de clase en la definición de la misma:  
```python
class MiClase():

    atributo_de_clase = valor
    otro_atributo_de_clase = None
```

Serán accesibles desde la clase, y desde cualquier instancia que no tenga un atributo de instancia llamado igual.  
```python
MiClase.atributo_de_clase
obj = MiClase()
obj.atributo_de_clase
```

Los atributos de instancia se definen de manera dinámica cuando se asignan por primera vez. Se puede hacer en la definición de la clase, o en cualquier método:  
```python
class MiClase():

    def __init__(self, valorNuevo):
        self.variable_de_instancia = valorNuevo
```

Y también se definen atributos dinámicamente cuando se utiliza el objeto: `una_instancia.un_atributo = un_valor`  
Esto se puede hacer en algún método dentro del mismo objeto, o en cualquier otro objeto donde se esté usando la instancia. Esto permite tener instancias distintas de una misma clase que tengan distintos atributos entre sí.


TODO: ver vars()

## Métodos como atributos - Decorador @property

Se pueden definir métodos para ser usados como atributos:  
```python
class MiClase():

    __variable_privada = None

    @property
    def variable_privada(self):
        # getter
        return self.__variable_privada

    @variable_privada.setter
    def variable_privada(self, valor):
        # setter
        self.__variable_privada = valor
```

Permite hacer:  
```python
mi_objeto.variable_privada = un_valor  # setter
mi_objeto.variable_privada  # getter
```

## Herencia

```python
class MiClaseHija(MiClasePadre):

    def __init__(self, valorNuevo, otroValor):
        MiClasePadre.__init__(valorNuevo)
        self.otra_variable = otroValor

    def metodo(self):
        super().metodo()
```

Se puede definir herencia múltiple:  
```python
class MiClaseHija(MiClasePadre, OtraClasePadre):

    def __init__(self, valorNuevo, otroValor):
        passs
```


### Variables de clases predefinidas
TODO: completar  
__doc__  para objetos documentables: módulos, clases, métodos y funciones . se usa help(objeto)
__name__  
__module__  
__dict__

## TODO: objetos
- __init__()
- declaración de atributos dentro y fuera de la clase
- variables de clase
- https://www.youtube.com/playlist?list=PLP8GkvaIxJP0VAXF3USi9U4JnpxUvQXHx
- uso de _ y __ https://www.youtube.com/watch?v=ALZmCy2u0jQ
- métodos de clase con @classmethod y métodos estáticos con @staticmethod
- herencia y herencia múltiple
- sobreescribir métodos, uso de `super()`
- print string con __str__() y __repr__
- comparación redefiniendo __eq__
- diccionario de atributos con __dict__
- clases decoradoras y uso de __call__
- Dataclass
