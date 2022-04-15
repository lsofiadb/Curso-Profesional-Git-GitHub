## Flujos de trabajo profesionales :necktie:

### ¿Que es un pull request? :mailbox_with_mail:
 
En un entorno profesional por lo general se bloquea la rama principal: main/master (la cual es la única que se despliega en el servidor de producción), de tal forma que para enviar código a dicha rama es necesario que este pase por un code review, sin embargo con el fin de realizar pruebas de manera segura sin afectar el producto final (rama main) que pueden estar utilizando los usuarios bien sea en un entorno web o en una aplicación móvil, se suele crear una rama alterna llamada **staging develop** (la cual se despliega en un servidor distinto al de la rama principal, es decir de pruebas), en la cual se realizan las pruebas antes de hacer merge con la rama principal, la cual claramente se encuentra constante actualizada respecto a esta, y ya que se trata de una rama de pruebas, el código nuevo que se realiza por los desarrolladores se fusiona con esta rama, con el fin de evitar inconvenientes directamente con la rama de desarrollo final; la acción de validar código antes de hacer merge con la rama staging develop, se conoce como **pull request** . En el proceso de validación entran a jugar diversos factores como lo pueden ser Builds (validaciones automáticas), asignación de código en tareas (metodología SCRUM), validaciones manuales por parte del equipo, despliegues, etc. 

:briefcase: Una vez se hace el merge con la rama staging develop es posible hacer merge de esta con la rama principal, para lo cual tambien se suele crear otro pull request. La persona encargada de gestionar todo ese proceso de revisión de código y de aprobar los pull request se conoce como **Desarrollador DevOps (Developer Operations)**: administrador del entorno de desarrollo que hace que los equipos trabajen de una manera más efectiva.

**NOTA** :round_pushpin: los pull request no son una característica de git sino de GitHub, ya que se enfoca en el trabajo colaborativo, sin embargo otros entornos como GitLab o Bitbucket tambien lo utilizan.  

## Utilizando imágenes en repositorios :camera:

Algo importante a tener en cuenta es que las imagenes son archivos binarios por ello cuando se suben a un repositorio y posteriormente se les realizan cambios, es necesario cargar el archivo COMPLETO nuevamente a git, lo cual es muy ineficiente, porque conforme más cambios se realicen el peso de estos archivos binarios tambien va a aumentar, haciendo cada vez más pesado el repositorio, sin embargo es posible almacenar estas imagenes en el repositorio de GitHub, al hacer esto lo que sucede en ocasiones es que se genera una memoria cache que no permite visualizar los cambios al instante de la imagen, por ello para limpiar este cache y forzar la actualización en el navegador basta con ejecutar el comando:

```
ctrl+shift+r
```
Otro comando que tambien lo permite es:
```
ctrl+F5
```

Para solucionar el problema de tildes basta con añadir la etiqueta:
```
<meta charset=“UTF-8”>
```
dentro del head del HTML. 


**NOTA** :construction: no olvidar realizar:
```
git pull origin nombreRama
```
antes de enviar cambios a esa rama en el repositorio remoto. 

## Utilizando Pull Requests (PR) en GitHub

Un PR es una funcionalidad de github (en gitlab llamada merge request y en bitbucket push request), en la que un colaborador pide que revisen sus cambios antes de hacer merge a una rama, normalmente master/main.

Al hacer un pull request se genera una conversación que pueden seguir los demás usuarios del repositorio, así como autorizar y rechazar los cambios.

El flujo del pull request es el siguiente: 

- Se trabaja en una rama paralela los cambios que se desean:
    ```
    git checkout -b <rama>
    ```
- Se hace un commit a la rama:
    ```
    git commit -am "Comentario"
    ```
- Se suben al repositorio remoto los cambios:
    ```
    git push origin <rama>
    ```
- En GitHub se hace el pull request comparando la rama master con la rama del fix.
- Uno o varios colaboradores revisan que el código sea correcto y dan feedback (en el chat del pull request)
- El colaborador hace los cambios que desea en la rama y lo vuelve a subir al remoto (automáticamente jala la historia de los cambios que se hagan en la rama, en remoto)
- Se aceptan los cambios en GitHub
- Se hace merge a master desde GitHub
- Importante :warning: cuando se modifica una rama, también se modifica el pull request.
