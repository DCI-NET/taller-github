# Ejercicio 1

En este ejercicio se va a crear un nuevo directorio y se inicializará un sistema
de control de versiones (SCV) con git.

## Paso 1. Crear el directorio.

### Para Windows:

Crear un directorio directamente con el explorador, o si se está usando
[git for Windows](https://gitforwindows.org/) ejecutar el siguiente comando

    mkdir ejercicio_1

### Para Linux / macOS:

Abrir una terminal y ejecutar el siguiente comando

    mkdir ejercicio_1

## Paso 2. Crear el SCV.

Una vez creado el directorio cambiarse a este
    
    cd ejercicio_1

y luego **inicializarlo**

    git init

y se podrá observar algo semejante al siguiente resultado

    Initialized empty Git repository in /home/edwinb/ejercicio_1/.git/

:tada: ¡Felicidades! Haz creado tu primer repositorio con SCV.

## Paso 3. Crea un archivo.

Asegurándose que se está trabajando dentro del directorio `ejercicio_1/` crear un archivo de Python
con el nombre `ejercicio_1.py` que contenga el siguiente comando

```python
import this
```

y ejecutarlo

    python ejercicio_1.py

para obtener _El Zen de Python_ :snake:

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
```

En caso de **no** tener Python instalado localmente, solamente basta con crear el archivo. En realidad
no es importante ejecutarlo, solamente es importante el archivo.

## Paso 4. ¿Qué sucedió en el SCV?

Dentro del directorio `ejercicio_1/` ejecutar el siguiente comando

    git status

para observar lo siguiente

```
On branch master

No commits yet

Untracked files:
(use "git add <file>..." to include in what will be committed)
        ejercicio_1.py

nothing added to commit but untracked files present (use "git add" to track)
```

Ahora el archivo está siendo _grabado_ por el SCV, y `git` avisa que existe un cambio importante que
debe ser registrado.

## Paso 5. Registrar los cambios

Hay dos formas de registrar los cambios. Primero

    git add .

este comando _propone_ que **todos** los archivos dentro del directorio tienen un cambio sustancial.

O bien, se puede hacer

    git add ejercicio_1.py

para _proponer_ que solamente se contemple el archivo en cuestión, en este caso `ejercicio_1.py`.

Finalmente, ejecutar nuevamente

    git status

y se obtendrá la respuesta

```
On branch master

No commits yet

Changes to be committed:
(use "git rm --cached <file>..." to unstage)
        new file:   ejercicio_1.py
```