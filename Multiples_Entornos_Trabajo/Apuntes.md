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

El stashed nos sirve para guardar cambios para después, Es una lista de estados que nos guarda algunos cambios que hicimos en Staging para poder cambiar de rama sin perder el trabajo que todavía no guardamos en un commit

Ésto es especialmente útil porque hay ocasiones en las que no se permite cambiar de rama, ésto porque porque tenemos cambios sin guardar, no siempre es un cambio lo suficientemente bueno como para hacer un commit, pero no queremos perder ese código en el que estuvimos trabajando.

El stashed nos permite cambiar de ramas, hacer cambios, trabajar en otras cosas y, más adelante, retomar el trabajo con los archivos que teníamos en Staging pero que podemos recuperar ya que los guardamos en el Stash.



