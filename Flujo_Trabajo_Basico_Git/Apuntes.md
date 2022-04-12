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