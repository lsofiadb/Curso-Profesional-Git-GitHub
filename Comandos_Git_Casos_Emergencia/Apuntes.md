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