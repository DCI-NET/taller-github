# Ejercicio 2 :computer:

Ahora se verá cómo se revierten cambios, se quitan propuestas y se
utiliza al máximo el poder de `git`.

## :heavy_plus_sign: Paso 1. Modificar un archivo.

En el mismo directorio que antes `taller_github/` posicionarse dentro y ejecutar

    git status

y se observará lo siguiente

```
On branch master
nothing to commit, working tree clean
```

Esto es lo que **siempre** se debe ver cuando no existen cambios en el directorio.

Ahora se va a modificar el archivo `ejercicio_1.py` para que contenga lo siguiente

```python
import this
print()
import __hello__
```

y se obtendrá lo siguiente

```
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!

Hello world!
```

A diferencia de antes, ahora se tiene un nuevo resultado, el archivo cambió. Si se ve el estado
del repositorio

    git status -sb

ahora se obtiene lo siguiente

```
## master
M ejercicio_1.py
```

notificando que el archivo ha sido (M)odificado, en la _rama_ `master`.

## :wrench: Paso 2. Proponer modificaciones (y revertirlas).

Ahora se proponen las modificaciones como antes

    git add .

para obtener lo siguiente

```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   ejercicio_1.py
```

Quizás este cambio **no** es tan importante, y se preferiría dejar solamente el
nuevo resultado, por lo que se pueden _revertir_ las propuestas con el comando

    git reset

lo que hará que **todo** se revierta. Si se quiere revertir solamente un archivo se usa

    git reset -- ejercicio_1.py

de cualquier forma se observa el siguiente resultado

```
Unstaged changes after reset:
M       ejercicio_1.py
```

lo que nos indica que todos los cambios propuestos serán _revertidos_.

## :pencil2: Paso 3. Modificar el archivo correctamente.

Se modificará nuevamente el archivo `ejercicio_1.py` con el siguiente contenido

```python
import __hello__
```

se _propone_ el cambio

    git add .

y se _registra_ con un mensaje

    git commit -m "Se cambió el Zen de Python por el Hola Mundo, es más corto."

El estado del repositorio revela que se ha hecho un nueva versión del archivo, muy diferente ahora

```
commit e21254cf268d3a6dcfab72c5cd23803283758326 (HEAD -> master)
Author: Edwin <developeredwin@gmail.com>
Date:   Sun Sep 15 19:15:46 2019 -0500

    Se cambió el Zen de Python por el Hola Mundo, es más corto.

 ejercicio_1.py | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

```