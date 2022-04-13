## Flujo de trabajo básico en Git

### Comandos para trabajo remoto con git:

Para clonar un repositorio:
```
git clone url_del_servidor_remoto
```

Para enviar los últimos commits al repositorio remoto (GitHub, Bitbucket, GitLab, etc):
```
git push
```

Para traer los últimos cambios del servidor remoto al repositorio local

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

 Otros comandos que nos para trabajar en proyectos muy grandes:

Muestra el id commit y el título del commit.
 ```
git log --oneline
```

 Muestra donde se encuentra el head point en el log.
```
git log --decorate
```

Explica el número de líneas que se cambiaron y muestra que se cambió en el contenido.
```
git log -p
```


```
git shortlog
```

```
git log --graph --oneline --decorate
```

```
git log --pretty=format
```

```
git log -3
```

```
git log --after=“2018-1-2”
```

```
git log --after=“today”
```

```
git log --author=“Name Author”
```

```
git log --grep=“INVIE”
```

```
git log --grep=“INVIE” –i
```

```
git log – index.html
```

```
git log -S “Por contenido”
```

```
git log > log.txt
```

---

Para hacer git add . y git commit -m "mensaje" al tiempo (siempre y cuando los archivos ya se les haya realizado git add . minimo una vez previamente, si se trata de archivos recien creados no funcionará):

```
git commit -am "mensaje"
```

## Retomando ramas - brances

Para crear una rama nueva:

```
git branch nombre
```

Para cambiar a otra rama:

```
git checkout otraRama
```

Para crear una rama y moverse a ella automáticamente, es decir, es la combinación de git brach y git checkout al mismo tiempo:

```
git checkout -b rama
```

Nos lleva a cualquier commit no importa la rama, ya que identificamos el id del tag, eliminando el historial de los commit posteriores al tag seleccionado.
```
git reset id-commit
```

Nos lleva a cualquier commit sin borrar los commit posteriores al tag seleccionado.
```
git checkout rama-o-id-commit
```

Este comando permite ver las ramas que se tienen:
```
git branch
```

