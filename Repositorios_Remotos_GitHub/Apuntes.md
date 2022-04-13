## Repositorios remotos: GitHub :octocat:

Para enlazar un repositorio local a uno remoto a través de su URL sin necesidad de clonarlo:

```
git remote add origin URL
```

Para visualizar que repositorio remoto está enlazado con el local:

```
git remote
```

```
git remote -v
```

Para enviar cambios desde el repositorio local al remoto:

```
git push origin nombreRama
```

```
git push origin main
```

Para traer los cambios del repositorio remoto al local:

```
git pull origin nombreRama
```

```
git pull origin main
```

**NOTA:** puede presentarse el siguiente error en el caso de que se estuviera trabajando con un repositorio local y mucho tiempo despues se quisiera enlazar su contenido con un repositorio remoto, de tal forma que no existen archivos comunes entre si, por ello, es necesario usar el siguiente comando:

**ERROR:**

```
fatal: resufing to merge unrelated histories
```
**SOLUCIÓN:**
```
git pull origin main --allow-unrelated-histories
```

Lo que se esta realizando a través del comando anterior es hacer un merge entre la versión local y remota, de tal forma que se integren ambos grupos de cambios, por ello abrirá el editor Vim para ingresar el mensaje del commit y finalizar el merge. 

Para traer los cambios de todas las ramas del repositorio remoto:

```
git fetch --all
```

Para ver las ramas locales:
```
git branch
```

Para ver las ramas remotas:
```
git branch -r
```

Para ver todas las ramas:

```
git branch -a
```


## LLaves públicas y privadas - cifrado asimétrico :key: :lock:

La llave pública se usa para cifrar el mensaje, si alguien intercepta el proceso de comunicación y captura el mensaje cifrado, no podrá descifrarlo ya que no tendrá la llave privada para hacerlo, por eso esta debe ser secreta. 

