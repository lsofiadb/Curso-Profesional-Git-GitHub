# *Introducción a Git*
## *¿Qué es Git?*
Es el Sistema de Control de Versiones (SCV) más popular, creado por *Linus Torvalds*.
Básicamente permite detectar los cambios realizados en archivos de texto plano, los cuales son distintos a los archivos binarios que contienen otros detalles adicionales como color, imagenes, etc.
### *Comandos básicos git*
---
Inicializar un repositorio nuevo:

```
	git init
```

Realizar seguimiento de los cambios de un archivo, es decir que esta información entra al **stage area**:

```
	git add archivo.txt
```

Realizar seguimiento de los cambios de todos los archivos de ese repositorio:

```
	git add .
```

Enviar los últimos cambios del archivo a la base de datos del sistema de control de versiones, para controlar los cambios que se le hayan hecho:

```
	git commit -m "mensaje"
```

Permite saber cuales archivos fueron añadidos al **stage area** y cuales no:

```
	git status
```

Muestra  todos los cambios realizados, incluyendo las lineas que se han cambiado, cuando y quién hizo estos cambios:

```
	git show
```

Para visualizar la historia completa de un archivo:

```
	git log archivo.txt
```

Enviar los cambios a un repositorio remoto como GitHub, Bitbucket, etc:

```
	git push 
```

Agrega los cambios del commit más reciente del repositorio remoto al repositorio local:

```
	git pull
```

### *Comandos básicos terminal de comandos*
---

Ir a la raiz del disco:

```
	cd /
```

Mostrar todos los archivos, incluso los ocultos en una lista:

```
	ls -al
```

Mostrar todos los archivos, incluso los ocultos en un grupo solamente:

```
	ls -a
```

Limpiar la consola:

```
	clear
    CTRL+L
```

Ir al disco c desde la raiz del disco:

```
	cd /c
```

**NOTA:** en Windows no se distingue entre mayúsculas y minúsculas en cuanto al nombre de archivos o carpetas, en cambio para Linux o Mac si es diferente. 


Crear directorio/carpeta:

```
	mkdir nombre
```

Crear archivo:

```
	touch archivo.txt
```

*Orientación en carpetas*

--- 
Carpeta actual:

```
	cd . 
```

Carpeta anterior:

```
	cd .. 
```
---

Visualizar contenido de un archivo por consola/terminal con el comando cat :cat: 

```
	cat archivo.txt
```


Visualizar lista de comandos ejecutados en la terminal:

```
	history
```

Si se quiere ejecutar un comando de esa lista:

```
	!<Número del comando en la lista de history>

    Ejemplo:
    !15
```


Borrar un archivo:

```
	rm archivo.txt
```

Información del funcionamiento de un comando:

```
	comando --help
```


