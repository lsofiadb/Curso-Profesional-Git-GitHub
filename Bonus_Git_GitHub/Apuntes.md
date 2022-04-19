# Bonus sobre Git y GitHub 

## Comandos y recursos colaborativos en Git y GitHub

Muestra cuantos commit ha hecho cada miembro del equipo:

```
git shortlog -sn
```

Muestra cuantos commit ha hecho cada miembro del equipo hasta los que han sido eliminado:
```
git shortlog -sn --all
```

Muestra cuantos commit ha hecho cada miembro quitando los eliminados sin los merges:

```
git shortlog -sn --all --no-merges
```

Utilizando alias en la configuración global de git:
```
git config --global alias.nombreAlias "comando"
```

```
git config --global alias.stats "shortlog -sn --all --no-merges"
```
Es decir que bastara con llamar git stats.

Muestra quien hizo cada cosa linea por linea:
```
git blame ARCHIVO
```

Para verlo mucho mejor:

```
git blame -c ARCHIVO
```

Para ver documentación de un comando en el navegador.
```
git blame --help
```

Muestra quien hizo cada cosa linea por linea indicándole desde que linea ver,  por ejemplo -L35,50:

```
git blame ARCHIVO -Llinea_inicial,linea_final
```
```
git blame ARCHIVO -L35,50
```

Y para añadirle mayor formato:
```
git blame ARCHIVO -L35,50 -c
```

Se muestran todas las ramas remotas:
```
git branch -r 
```

Se muestran todas las ramas tanto locales como remotas:
```
git branch -a
```