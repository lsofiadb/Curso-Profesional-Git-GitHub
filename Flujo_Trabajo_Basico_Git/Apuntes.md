## Flujo de trabajo básico en Git :rowboat:

### Comandos para trabajo remoto con git:

Para clonar un repositorio:
```
git clone url_del_servidor_remoto
```

Para enviar los últimos commits al repositorio remoto (GitHub, Bitbucket, GitLab, etc):
```
git push
```

Para traer los últimos cambios del servidor remoto al repositorio local:

```
git fetch
```

Para combinar los últimos cambios del repositorio remoto con los del repositorio local:
```
git merge
```

Permite combinar git fetch y git pull:

```
git pull
```

 Otros comandos frecuentemente usados al trabajar en proyectos muy grandes :office:
 ---

Muestra el id commit y el título del commit:
 ```
git log --oneline
```

 Muestra donde se encuentra el head point en el log:
```
git log --decorate
```

Explica el número de líneas que se cambiaron y muestra que se cambió en el contenido:
```
git log -p
```

Indica que commits ha realizado un usuario, mostrando el usuario y el título de sus commits:
```
git shortlog
```

Muestra mensajes personalizados de los commits:
```
git log --graph --oneline --decorate
```
Muestra los commits realizados con su fecha:
```
git log --pretty=format:"%cn hizo un commit %h el dia %cd"
```

Se limita la cantidad de commits a mostrar, en este caso son 3:

```
git log -3
```

Muestra los commits a partir de una fecha en especifico:

```
git log --after=“2018-1-2”
```

```
git log --after=“yesterday”
```

Commits hechos por autor que cumplan exactamente con el nombre:

```
git log --author=“Name Author”
```
Busca los commits que cumplan tal cual está escrito entre las comillas:
```
git log --grep=“INVIE”
```

Busca los commits que cumplan sin importar mayúsculas o minúsculas.
```
git log --grep=“INVIE” –i
```

Busca los commits en un archivo en específico:
```
git log index.html
```

Buscar los commits con el contenido dentro del archivo:
```
git log -S “Por contenido”
```

Guardar los logs en un archivo txt:
```
git log > log.txt
```

---

Para hacer git add . y git commit -m "mensaje" al tiempo (siempre y cuando los archivos ya se les haya realizado git add . minimo una vez previamente, si se trata de archivos recien creados no funcionará):

```
git commit -am "mensaje"
```

## Retomando ramas - branches :herb:

Para crear una rama nueva:

```
git branch nombre
```

Para cambiar a otra rama:

```
git checkout otraRama
```

Para crear una rama y moverse a ella automáticamente, es decir, es la combinación de git branch y git checkout al mismo tiempo:

```
git checkout -b rama
```

Nos lleva a cualquier commit no importa la rama, ya que identificamos el id del tag, eliminando el historial de los commit posteriores al tag seleccionado.
```
git reset id-commit
```

Nos lleva a cualquier commit sin borrar los commit posteriores al tag seleccionado:

```
git checkout rama-o-id-commit
```

Este comando permite ver las ramas que se tienen:

```
git branch
```

Para fusionar dos ramas, teniendo en cuenta que se hace merge desde la rama a la cual se le quieren aplicar los nuevos cambios:

```
git merge otraRama
```

Es necesario tener presente que si se generan conflictos deben repararse y posteriormente hacer un commit, para finalizar el merge. Editores como VSC permiten visualizar estos conflictos y solucionarlos. Sin embargo es recomendable no editar el mismo archivo a la vez, esto suele ocurrir en casos de emergencia. 

NOTA:pushpin::date: desde el 1 de octubre de 2020 GitHub cambió el nombre de la rama principal: ya no es “master” sino main. Este derivado de una profunda reflexión ocasionada por el movimiento #BlackLivesMatter.
