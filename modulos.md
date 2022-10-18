# Módulos, paquetes y librerías

Más: 
- <https://towardsdatascience.com/understanding-python-imports-init-py-and-pythonpath-once-and-for-all-4c5249ab6355>
- <https://pywombat.com/articles/modulos-paquetes-python>

### Módulo

Un módulo es un archivo, que puede importarse en otro módulo, y se puede acceder a sus funciones, variables y demás objetos.

```python
import un_modulo
import un_modulo_distinto as un_alias

un_modulo.funcionDefinida()

un_modulo_distinto.otraFuncion(parametro)

un_alias.una_variable
```

Se pueden importar objetos de manera separada de un determinado módulo, y usarlo directamente:

```python
from un_modulo import unaFuncion
from un_modulo import unObjeto as unAliasDeObjeto
from un_modulo_distinto import unaVariable as un_alias, otroObjeto as otro_alias
```

Importar todos los objetos de un módulo: `from un_modulo import *`  
No se recomienda su uso porque puede resultar confuso.

### Paquete

Un paquete es un módulo que contiene adentro otros módulos. Generalmente un directorio será un paquete (módulo principal) y sus archivos los módulos (secundarios).
Se puede importar un paquete como un módulo más, o importar un submódulo.

```python
import un_modulo_principal
import un_modulo_principal.un_submodulo
```

### Librería

Una librería es un conjunto de módulos y paquetes agrupados con un fin determinado.

### Contexto de ejecución

El atributo `__name__` se asigna a un módulo cuando es invocado, y permite determinar en qué contexto se está ejecutando.

Si el módulo es el principal, el nombre será `__main__`, de lo contrario el nombre será el propio del archivo.

```python
if __name__ == "__main__":
    # sólo se ejecuta si fue invocado en forma directa, o sea es el módulo principal
    pass
```
