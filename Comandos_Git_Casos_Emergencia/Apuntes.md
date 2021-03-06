# Comandos de Git para casos de emergencia :rotating_light::rotating_light::rotating_light:

## Reconstruir commits en Git con amend :high_brightness:

A veces hacemos un commit, pero resulta que no queríamos mandarlo porque faltaba algo más. Utilizamos git commit --amend, amend en inglés es remendar y lo que hará es que los cambios que hicimos nos los agregará al commit anterior.

```
git commit --amend
```

Consideraciones :pencil2:

- Los nuevos cambios deben estar añadidos al staging area con git add .
- Es posible modificar la descripción del commit, ya que al ejecutar el comando nos abre el editor de vim para editarlo.
- Nos mantiene un solo commit, es decir que el "error" queda invisible en el historial de commits :+1:

## Git Reset y Reflog: úsese en caso de emergencia :loudspeaker:

¿Qué pasa cuando todo se rompe y no sabemos qué está pasando? Con git reset HashDelHEAD nos devolveremos al estado en que el proyecto funcionaba.

Sin embargo en el log habitual puede que no aparezca el hash del HEAD al que queremos volver, por ello existe un comando que almacena el historial COMPLETO de todo lo que se ha realizado, incluso de los git reset, es decir que mediante el podemos regresar todo a como lo teniamos originalmente funcional, accediendo al hash del commit al que queremos volver. Primero utilizamos:

```
git reflog
```

Alli podremos visualizar la lista completa de logs con su correspondiente HASH.

Y a partir de esto podemos utilizar:

- git reset --soft HashDelHEAD te mantiene lo que tengas en staging ahí.
- git reset --hard HashDelHEAD resetea absolutamente todo incluyendo lo que tengas en staging.

Tambien es posible volver a un head especifico a traves de:

```
git reset HEAD@{4}
```
Este último comando se considera como un git reset --soft, ya que permite mostrar el estado en staging de los cambios de ese último commit pero no suele arreglar todo el problema. Por ello se suele utilizar un git reset --hard.

Los comandos git reset ya se habian visto previamente, sin embargo cabe recordar que es una MALA práctica utilizarlo, debe ser la última opción a considerar. 

**NOTA**: aunque en git log no aperezcan los commits en donde se daño todo, si se utiliza git reflog si se observara el historial completo, esto ya que git no borra nada :bulb:


## Buscar en archivos y commits de Git con Grep y log :mag_right:

A medida que nuestro proyecto se hace grande vamos a querer buscar ciertas cosas.

Por ello surgen comandos muy utiles!! :bulb:

Para buscar una palabra dentro de los archivos del proyecto:

```
git grep <palabra>
```
```
git grep color
```
El comando anterior nos buscará en todo el proyecto los archivos en donde está la palabra color.

```
git grep -n color
```
Este último comando nos mostrará un output adicional indicando en qué línea está lo que estamos buscando.

```
git grep -c color
```
El comando anterior nos dirá cuántas veces se repite esa palabra y en qué archivo.

Si queremos buscar cuántas veces utilizamos un atributo de HTML lo hacemos con: 

```
git grep -c "<p>"
```

A su vez si queremos visualizar los commits que involucran cierta palabra se utiliza:

```
git log -S "footer"
```

Sin embargo ya el git log -S “palabra” no trae el conteo, solo trae las palabras parecidas a las que estamos buscando.

Es mejor que utilizar:
```
git log --all --oneline | grep "apuntes"
```
Lo cual traerá los commits en donde se encuentra la palabra.