# Ejercicio 3 :recycle:

En este ejercicio se verá cómo revisar la _historia_ del repositorio,
y regresar a estados anteriores.

## :rewind: Paso 1. Revisar estados anteriores.

Primero, asegurarse de estar en el directorio `taller_github/` y luego
ejecutar el siguiente comando

    git log

y nos dará la historia completa del repositorio

```
commit e21254cf268d3a6dcfab72c5cd23803283758326 (HEAD -> master)
Author: Edwin <developeredwin@gmail.com>
Date:   Sun Sep 15 19:15:46 2019 -0500

    Se cambió el Zen de Python por el Hola Mundo, es más corto.

commit b0bc0d83c81dbff102b1966a33ead229f8d4e415
Author: Edwin <developeredwin@gmail.com>
Date:   Sun Sep 15 19:14:44 2019 -0500

    Mi primer archivo.
```

Las cadenas como `e21254cf268d3a6dcfab72c5cd23803283758326` son los **identificadores**
de cada uno de los cambios, y se puede accesar a su versión corta con el comando

    git log --oneline

y entonces resulta

```
e21254c (HEAD -> master) Se cambió el Zen de Python por el Hola Mundo, es más corto.
b0bc0d8 Mi primer archivo.
```

## :hourglass: Paso 2. ¡Regresar en el tiempo!

Ahora se quiere revisar lo que se tenía antes del nuevo cambio al archivo `ejercicio_1.py`. El cambió fue sustancial,
prácticamente se eliminó todo lo que se tenía. ¿Se puede volver a ver este archivo? ¡Por supuesto! Regresemos en el tiempo
con el siguiente comando

    git checkout b0bc0d8

donde `b0bc0d8` es el identificador del estado de la _primera_ versión del archivo. Recordar que este identificador se obtuvo
en el paso anterior.

`git` responde con el siguiente mensaje

```
Note: switching to 'b0bc0d8'.            
                                                                     
You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.
 
If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:
                                         
  git switch -c <new-branch-name>
      
Or undo this operation with:             
                                                                     
  git switch -                                                              
                                              
Turn off this advice by setting config variable advice.detachedHead to false
                                     
HEAD is now at b0bc0d8 Mi primer archivo.
```

Si ahora se revisa el contenido del archivo se observa lo siguiente

```python
import this
```

que corresponde a lo que se tenía antes de los cambios. ¡Se ha vuelto en el tiempo!


## :rotating_light: DECISIÓN IMPORTANTE

Ahora que se ha _regresado en el tiempo_ hay dos opciones: borrar todo lo que se tiene hasta ahora o crear una
**versión alternativa** (¡justo como en las películas!).

### :twisted_rightwards_arrows: Opción 1: Una nueva línea de tiempo. :watch:

Estando en el momento anterior se puede usar el siguiente comando

    git switch -c hola-mundo

donde `hola-mundo` es el nombre de una nueva _rama_ del repositorio.

Si ahora se modifica el contenido tal que tenga

```python
import this
print()
import __hello__
```

como antes se había realizado, los cambios ahora no afectarán al archivo anterior.

Se registran los cambios y se agrega un mensaje; con el siguiente comando se puede hacer todo de forma simultanea

    git commit -am "Se agregó el Hola Mundo que faltaba."

y el resultado es una nueva rama

```
[hola-mundo f73bb96] Se agregó el Hola Mundo que faltaba.
 1 file changed, 2 insertions(+)
```

y ahora existen dos ramas

```
* hola-mundo f73bb96 Se agregó el Hola Mundo que faltaba.
  master     e21254c Se cambió el Zen de Python por el Hola Mundo, es más corto.
```

que se pueden ver con el siguiente comando

    git branch -vv

### :twisted_rightwards_arrows: Opción 2: Reconstruir el universo :milky_way:

Si se desea _borrar_ **todo** lo que se ha hecho hasta ahora entonces se debe hacer lo siguiente. Ejecutar

    git switch -

estando en la bifurcación.

Luego, ejecutar

    git reset --hard b0bc0d8

y `git` nos responde con lo siguiente

    HEAD is now at b0bc0d8 Mi primer archivo.

Verificando el archivo, se tiene lo siguiente

```python
import this
```

pero ahora, ¡ya **no existe** una historia!

    git log

lo que resulta en

```
commit b0bc0d83c81dbff102b1966a33ead229f8d4e415 (HEAD -> master)
Author: Edwin <developeredwin@gmail.com>
Date:   Sun Sep 15 19:14:44 2019 -0500

    Mi primer archivo.
```

y a partir de aquí modificar el archivo tal que se tiene lo que se requiere

```python
import this
print()
import __hello__
```

y se proponen y registran los cambios

    git commit -am "Se borraron los cambios y se agregaron en el archivo."

Se obtiene el siguiente mensaje

```
[master b6dbe8c] Se borraron los cambios y se agregaron en el archivo.
 1 file changed, 2 insertions(+)
```