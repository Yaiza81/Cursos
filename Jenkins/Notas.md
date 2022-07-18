# Jenkins

Repositorio de Ejemplos:
- https://github.com/elbuo8/platzi-scripts


Job

- Discard old builds : para conservar solo ciertos builds
- Disable this project: para desabilitar los jobs cuando se produce un error 
- Build after other projects are built: para dependencias como workflow

** Delete workspace before build starts : siempre marcarlo para evitar conflictos.

Plugins

Parameterized Trigger plugin 
- Dependencias entre jobs

Github
- Conexión con webhook (Manual) no es lo mas recomendable
- Usar replay en un build ya ejecutado para poder modificar el jenkinsfile sin modificar desde git 

