# Múltiples entornos de trabajo :office: :post_office: :european_post_office:

## Git Rebase: reorganizando el trabajo realizado 

El comando rebase es una **mala práctica**, **nunca** se debe usar :x: :x: :x: :x:

Básicamente con rebase puedes recoger todos los cambios confirmados en una rama y ponerlos sobre otra directamente. Sin  embargo esta reescribiendo la historia del repositorio.

Rabase es una forma de hacer cambios silenciosos en una rama.

Presenta bastantes problemas:

- No queda el historial de los cambios originales.

- No se sabe el autor real de los commits.

- Si la rama principal avanzo varios commits puede generar varios conflictos que se tendrán que solucionar de manera manual. 

Solo suele utilizarse en repositorios locales y en casos de emergencia, para usar rebase primero se realiza en la rama que tiene los cambios y luego en la rama final donde que quieren fusionar esos cambios, es decir donde quedaran finalmente.

```
git rebase experimento
```
En donde experimento surge a partir de main.

```
git rebase main
```
A continuación se observan las principales diferencias entre el comando Merge y Rebase en git: 

<img src="https://github.com/lsofiadb/Curso-Profesional-Git-GitHub/blob/main/Imagenes/Rebase-vs-Merge-info.jpg" >


## Git Stash: guardar cambios en memoria y recuperarlos después :hourglass: :arrows_counterclockwise: :hourglass_flowing_sand:

El stashed nos sirve para guardar cambios para después, es una lista de estados que nos guarda algunos cambios que hicimos en Staging para poder cambiar de rama sin perder el trabajo que todavía no guardamos en un commit

Ésto es especialmente útil porque hay ocasiones en las que no se permite cambiar de rama, ésto porque porque tenemos cambios sin guardar, no siempre es un cambio lo suficientemente bueno como para hacer un commit, pero no queremos perder ese código en el que estuvimos trabajando.

El stashed nos permite cambiar de ramas, hacer cambios, trabajar en otras cosas y, más adelante, retomar el trabajo con los archivos que teníamos en Staging pero que podemos recuperar ya que los guardamos en el Stash.

### git stash

Este comando nos permite guardar los cambios en una lista diseñada para ser temporal llamada Stash, para posteriormente recuperarlos cuando queramos. Para agregar los cambios al stash se utiliza el comando:

```
git stash
```

Podemos poner un mensaje en el stash, para asi diferenciarlos en git stash list por si tenemos varios elementos en el stash. Ésto con:

```
git stash save "mensaje identificador del elemento del stashed"
```

### git stash list

Para ver la lista (esta se comporta como una estructura de datos tipo LIFO) de cambios guardados en Stash y así poder recuperarlos o hacer algo con ellos podemos utilizar el comando:

```
git stash list
```

### Recuperar elementos del git stash list con pop
Una vez estan guardados los cambios podemos movernos a otra rama y hacer lo que necesitemos, para cuando estemos listos de retomar los cambios que guardamos, regresamos a la rama en que estabamos trabajando y ejecutamos el comando:
```
git stash pop
```
```
git stash pop stash@{<num_stash>}
```
El método pop recuperará y sacará de la lista el último estado del stashed y lo insertará en el staging area, por lo que es importante saber en qué branch te encuentras para poder recuperarlo, ya que el stash será agnóstico a la rama o estado en el que te encuentres, siempre recuperará los cambios que hiciste en el lugar que lo llamas.


### Eliminar elementos del stash con drop
Cuando nos equivocamos al crear un stash y no querermos usarlo, es decir revertir los cambios, se usa:
```
git stash drop
```

Pero si en cambio conoces el índice del stash que quieres borrar (mediante git stash list) puedes utilizar el comando:

```
git stash drop stash@{<num_stash>}
```

### Eliminar TODOS los elementos del stash
```
git stash clear
```

## Consideraciones :pushpin:

- El cambio más reciente (al crear un stash) SIEMPRE recibe el valor 0 y los que estaban antes aumentan su valor.
- Al crear un stash tomará los archivos que han sido modificados y eliminados. Para que tome un archivo creado es necesario agregarlo al Staging Area con git add [nombre_archivo] con la intención de que git tenga un seguimiento de ese archivo, o también utilizando el comando git stash -u (que guardará en el stash los archivos que no estén en el staging).
- Al aplicar un stash este no se elimina, es buena práctica eliminarlo.

## Otro comando muy útil para manejar git stash con ramas

Si se quiere crear una rama con los cambios guardados en el último stash:
```
git stash branch <nombre_de_la_rama>
```

## Git Clean: limpiar tu proyecto de archivos no deseados :put_litter_in_its_place:

A veces creamos archivos cuando estamos realizando nuestro proyecto que realmente no forman parte de nuestro directorio de trabajo, que no se deberían agregar y lo sabemos.

Es importante tener en cuenta que git clean solamente considera borrar archivos redudantes, pero no carpetas, para estas si es necesario borrarlas manualmente, además claramente no tiene en cuenta aquellos archivos que se incluyeron en el .gitignore del proyecto.

Para saber qué archivos vamos a borrar utilizamos:
```
git clean --dry-run
```

Para borrar todos los archivos listados (que no son carpetas) utilizamos:
```
git clean -f
```
