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

Con el fin de tener mayor seguridad, se crearan estas dos llaves en la máquina local de tal forma que la comunicación con GitHub sea a través del protocolo SSH y no HTTPS.

A la llave privada se le puede añadir una contraseña adicional encima para hacerla aún más segura.

Para generar llaves SSH(Secure Shell) nos dirijimos al home (raiz del disco dentro de un usuario) y mediante git bash:

```
ssh-keygen -t rsa -b 4096 -C "tu@email.com"
```

Ahora sugiere añadir una ruta de carpeta distinta pero se puede seleccionar la que se sugiere en la terminal, basta con dar enter.

Allí añadirá dos archivos con el mismo nombre:
id_rsa, sin embargo el archivo que contiene extensión .pub es el que corresponde a la llave pública, el otro es el de la llave privada.

Para terminar de configurar el sistema, es necesario el encender el servidor SSH de la computadora a través de:

```
eval $(ssh-agent -s)
```

La salida debe ser:

```
agent pid ID
```

HACK: Shortcut hacia el home:

```
cd ~
```

Para añadir llave SSH a este servidor:

```
ssh-add ruta-donde-guardaste-tu-llave-privada
```

La salida debe ser un mensaje que indique que la identidad fue añadida con el correo electrónico.


## Conexión a GitHub con SSH :closed_lock_with_key:

Es necesario añadir la clave pública al repositorio remoto de GitHub a través de settings, indicando un nombre a la computadora que tiene esa llave, puesto que si se tienen varios equipos, se debe crear un par de llaves por cada uno de ellos y se configurarán de igual forma en GitHub añadiendo una llave pública para cada uno de ellos.

Ahora para hacer uso del protocolo SSH, basta con escoger un repositorio local y modificarle el "origin" que se tenia previamente con HTTPS por el URL de SSH que aparece en GitHub:

```
git remote set-url origin url-ssh-del-repositorio-en-github
```

Al realizar nuevos cambios, antes de subirlos al repositorio remoto es necesario por buena práctica realizar git pull, con el fin de evitar conflictos, de esta forma estaremos constantemente actualizados de los últimos cambios de los demás desarrolladores.

## Tags y versiones en Git y GitHub

Un comando muy útil que permite observar un gráfico de como han evolucionado las distintas ramas :herb:

```
git log --all --graph
```

Sin embargo para visualizar unicamente el título del commit:

```
git log --all --graph --decorate --oneline
```

Sin embargo como es un comando MUY largo, es posible asignarle un alias para poder llamarlo de una manera más sencilla, para añadir el alias basta con:

```
alias arbolito="git log --all --graph --decorate --oneline"
```

### ¿Qué son los Tags? 

Los Tags permiten marcar un punto especifico de la historia de un proyecto (realeases :round_pushpin:) . De esta forma se puede hacer un seguimiento al progreso del proyecto e identificar los cambios más fácilmente entre cada versión. Incluso es posible hacer un checkout a un tag.

Para crear un Tag:

```
git tag -a v1.0 -m "Apuntes primera seccion del curso" IDCommit/HashCommit
```

Para visualizar los tags creados:

```
git tag
```

Para saber el ID de ese tag:

```
git show-ref --tags
```

Sin embargo ese ID es distinto al ID del commit enlazado. 

Una manera de ver realmente el commit enlazado es:

```
git show IDTag
```

Además al usar el comando git log, el historial de commits se mostrará tambien con el Tag asociado al lado de su HASH.

Los tags suelen ser muy útiles en GitHub para que los usuarios puedan dirijirse a los "realeases" de un proyecto directamente.

Aunque no se haga un cambio como tal es necesario subir estos tags a GitHub a través del comando:

```
git push origin --tags
```

Para **BORRAR** un tag:

```
git tag -d nombreTag
```

Sin embargo aunque este comando funcione localmente, al subir nuevamente los tags al repositorio remoto, el tag seguirá apareciendo, porque se suelen tener como referencia para los realeases, por ello es necesario hacer algo adicional para borrarlo completamente:

```
git push origin :refs/tags/nombreTagABorrar
```



