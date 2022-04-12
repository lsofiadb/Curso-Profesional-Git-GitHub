## *Comandos básicos git*
---
Para sacar un archivo del **stage area**, es decir antes de hacer el commit:

```
git rm --cached historia.txt
```

Otra opción:

```
git reset historia.txt
```

## Configuración del usuario en Git Bash

Visualizar todas las configuraciones:

```
git config
```

Visualizar todas las configuraciones por defecto de git en local:

```
git config --list
```

Establecer correo electrónico de GitHub:

```
git config --global user.email "lauraduenas1105@gmail.com"
```

Establecer el nombre del usuario:

```
git config --global user.name "Laura Sofia Dueñas Bulla"
```

*HACK* :dizzy:

Abrir un archivo en Visual Studio Code desde git bash:

```
code historia.txt
```

Visualizar los cambios que se hicieron de un archivo:

```
git show historia.txt
```

Añadir el mensaje del commit dentro del editor vim:

```
git commit
```

Cuando se abre el editor, para poder escribir el mensaje:

```
ESC+i
```

Para guardar el commit y cerrar el editor vim:

```
ESC+shift+zz
```

Visualizar diferencias entre las versiones de un archivo:

```
git diff IDCommit1 IDCommit2
Ejemplo:
git diff a9b7a1a15c450651dacd862801261bf790a7a5c0 f5ce290742633929584db1c441fb0e9186d2fb3b
```

**NOTA** :arrow_right: es necesario tener en cuenta el orden en que se ponen los IDs de los commits ya que para git el primer ID corresponde al commit más antiguo y el segundo ID corresponde a la versión más actual, de tal forma que en color blanco muestra las lineas que no cambiaron, en color rojo aquellas que se cambiaron o eliminaron y en color verde las que se añadieron. Todo esto respecto al ID del commit más antiguo. Claramente se pueden poner los IDs al contrario pero será más dificil comprender que fue lo que cambió respecto a la versión más actual. 

## Estados de los archivos en git
---
Esta imagen realizada por Julio Cardenas permite comprender mucho mejor los diferentes estados que puede tener un archivo en git:

<img src="https://github.com/lsofiadb/Curso-Profesional-Git-GitHub/blob/main/Imagenes/EstadosArchivosGitFuenteJulioCardenas.jpg" width="750px">


## Ramas - Branches :herb:
---
Una rama corresponde a una versión del código sobre el que se esta trabajando, con la serie de commits realizados.

Utilizar ramas permite mantener el orden en el control de versiones y manipular el código de manera segura.

Por defecto al inicializar un proyecto, se crea la rama Main o Master, también conocida como rama de producción.

Cuando se realizan experimentos se pueden generar ramas alternas a la rama principal, por lo general suelen llamarse como **development**, las cuales estan basadas en la rama principal, sin embargo permiten realizar modificaciones sin afectar la rama principal. 


Por otro lado cuando se encuentran errores en la rama principal, se suele crear una rama alterna llamada: **hotfix** o **bugfixing** para hacer las correspondientes modificaciones y pruebas para solucionar los errores, de tal forma que cuando estos cambios esten listos, se pueda fusionar esta rama con la rama principal, a través de una operación conocida como: **merge**.


**NOTA** :rotating_light: es importante tener en cuenta que si se modifica el mismo archivo en distintas ramas al momento de hacer merge con la rama principal se pueden presentar conflictos, ya que se tienen versiones diferentes de un mismo archivo y git no sabe cual escoger, por ello es necesario repararlos antes, puesto que no permitirá fusionar ambas ramas mientras permanezca el conflicto. 

## Volver en el tiempo usando reset :clock3: :arrow_right: :clock10:
---
Volver en el tiempo implica que no se puede regresar al futuro (último commit) y continuar con los cambios que se tenían, una vez se regresa se elimina el historial de commits. 

Existen dos tipos de reset:

- HARD :triangular_flag_on_post: :warning: permite regresar a una versión anterior eliminando **TODOS** los cambios que se habian hecho despues de ese commit, incluyendo lo que se tenga en **staging area**, por ello es necesario usarlo de manera cuidadosa ya que **NO** hay forma de recuperar esos cambios. Su sintaxis es así:

```
git reset IDCommit --hard
```

- SOFT :white_check_mark: permite regresar a una versión anterior pero los archivos que se tengan en **staging** permanecen allí, a diferencia de HARD, es decir que pueden ser enviados a un commit, sin embargo el historial de commits tambien desaparece. Su sintaxis es:

```
git reset IDCommit --soft
```

## Viajar en el tiempo usando checkout :clock3: :arrows_counterclockwise: :clock10:
---

Viajar en el tiempo implica poder regresar al pasado o al futuro sin eliminar el historial de commits, es muy útil cuando se quiere visualizar o modificar algún archivo en especifico sin modificar todo el proyecto.

Para visualizar un archivo en especifico en una versión anterior (esto añade ese archivo al staging area inmediatamente):

```
git checkout IDCommit archivo.txt
```

Tambien es posible recuperar todo el proyecto completo, no solamente un archivo:

```
git checkout IDCommit 
```

Para visualizar la ultima versión (regresar al futuro) de un archivo en una rama en especifico:

```
git checkout master archivo.txt
```


## Diferencias entre git rm y git reset
---

### **git rm**
Permite eliminar archivos de Git sin eliminarlos del historial de commits. Es decir que si se quiere recuperar el archivo basta con viajar en el tiempo y recuperarlo.

Para utilizar git rm es necesario añadir los siguientes flags de acuerdo a su propósito:

- Si se desea eliminar los archivos del staging area pero conservarlos en el directorio de trabajo y por tanto en el disco duro se utiliza:

	```
	git rm  --cached 
	```

	```
	git rm  --cached archivo.txt
	```
- Para eliminar los archivos de Git y del disco duro:

	```
	git rm  --force archivo.txt
	```

### **git reset**

Este comando permite volver en el tiempo. Pero no como git checkout en donde viajamos y volvemos. Con git reset se regresa al pasado sin la posibilidad de volver al futuro. Es decir que se borra la historia y no hay forma de recuperarla, es necesario sobreescribirla.

Como se habia mencionado anteriormente se puede utilizar la versión --hard o --soft, sin embargo existe uno adicional llamado **head** que permite sacar los archivos del staging area pero conservarlos en el directorio de trabajo y en el disco duro:

```
git reset head
```
```
git reset head archivo.txt
```
La siguiente imagen realizada por Freddy Barreiro permite sintetizar las diferencias entre git rm y git reset:

<img src="https://github.com/lsofiadb/Curso-Profesional-Git-GitHub/blob/main/Imagenes/GitRmVsGitResetFuenteFreddyBarreiro.jpg" width="750px">

## Diferencias entre distintos commits
---

Para visualizar las diferencias entre los archivos que se encuentran en **staging area** y los archivos **untracked** es decir que no han sido añadidos a través de **git add .** se utiliza el comando:

```
git diff
```

Para visualizar los cambios hechos en cada commit, en donde se indica la cantidad de bytes añadidos y eliminados:

```
git log --stat
```

**NOTA** :pushpin: si se tienen muchos commits con las flechas :arrow_down: :arrow_up:  se puede continuar visualizandolos, para salir de esta vista basta con escribir:

```
q
```
