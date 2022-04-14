## Flujos de trabajo profesionales :necktie:

### ¿Que es un pull request? :mailbox_with_mail:
 
En un entorno profesional por lo general se bloquea la rama principal: main/master (la cual es la única que se despliega en el servidor de producción), de tal forma que para enviar código a dicha rama es necesario que este pase por un code review, sin embargo con el fin de realizar pruebas de manera segura sin afectar el producto final (rama main) que pueden estar utilizando los usuarios bien sea en un entorno web o en una aplicación móvil, se suele crear una rama alterna llamada **staging develop** (la cual se despliega en un servidor distinto al de la rama principal, es decir de pruebas), en la cual se realizan las pruebas antes de hacer merge con la rama principal, la cual claramente se encuentra constante actualizada respecto a esta, y ya que se trata de una rama de pruebas, el código nuevo que se realiza por los desarrolladores se fusiona con esta rama, con el fin de evitar inconvenientes directamente con la rama de desarrollo final; la acción de validar código antes de hacer merge con la rama staging develop, se conoce como **pull request** . En el proceso de validación entran a jugar diversos factores como lo pueden ser Builds (validaciones automáticas), asignación de código en tareas (metodología SCRUM), validaciones manuales por parte del equipo, despliegues, etc. 

:briefcase: Una vez se hace el merge con la rama staging develop es posible hacer merge de esta con la rama principal, para lo cual tambien se suele crear otro pull request. La persona encargada de gestionar todo ese proceso de revisión de código y de aprobar los pull request se conoce como **Desarrollador DevOps**: administrador del entorno de desarrollo que hace que los equipos trabajen de una manera más efectiva.

**NOTA** :round_pushpin: los pull request no son una característica de git sino de GitHub, ya que se enfoca en el trabajo colaborativo, sin embargo otros entornos como GitLab o Bitbucket tambien lo utilizan.  



```

```
