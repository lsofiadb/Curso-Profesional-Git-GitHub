### *Comandos básicos git*
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

:ledger: **NOTA:** es necesario tener en cuenta el orden en que se ponen los IDs de los commits ya que para git el primer ID corresponde al commit más antiguo y el segundo ID corresponde a la versión más actual, de tal forma que en color blanco muestra las lineas que no cambiaron, en color rojo aquellas que se cambiaron o eliminaron y en color verde las que se añadieron. Todo esto respecto al ID del commit más antiguo. Claramente se pueden poner los IDs al contrario pero será más dificil comprender que fue lo que cambió respecto a la versión más actual. 

#### Estados de los archivos en git:
---
Esta imagen realizada por Julio Cardenas permite comprender mucho mejor los diferentes estados que puede tener un archivo en git:

![Estados](.//Imagenes//EstadosArchivosGitFuenteJulioCardenas.jpg)