# Tutorial de Git y GitHub
En este documento se explica el funcionamiento básico de git. 
El curso completo lo podemos encontrar en :
[youtube](https://www.youtube.com/watch?v=3GymExBkKjE)


# Índice

1. [Introducción](#introducción)
2. [Configuración Inicial](#configuración-inicial)
3. [Crear un Repositorio Git](#crear-un-repositorio-git)
4. [Ramas en Git](#ramas-en-git)
5. [Git Add y Commit](#git-add-y-commit)
6. [Historial de Cambios](#historial-de-cambios)
7. [Revertir Cambios](#revertir-cambios)
8. [Visualizaciones de Logs](#visualizaciones-de-logs)
9. [Alias en Git](#alias-en-git)
10. [Gitignore](#gitignore)
11. [Comparación de Cambios](#comparación-de-cambios)
12. [Desplazamiento entre Commits](#desplazamiento-entre-commits)
13. [Reset en Git](#reset-en-git)
14. [Etiquetas (Tags)](#etiquetas-tags)
15. [Eliminación de un Commit](#eliminación-de-un-commit)
16. [Trabajar con Ramas](#trabajar-con-ramas)
    - [Fusionar Ramas](#fusionar-ramas)
    - [Manejo de Conflictos](#manejo-de-conflictos)
17. [Git Stash](#git-stash)
18. [Integración de Cambios](#integración-de-cambios)
19. [Eliminar Ramas](#eliminar-ramas)
20. [Configuración de GitHub](#configuración-de-github)
    - [Configuración de GitHub en Windows](#configuración-de-github-en-windows)
    - [Visualización del Certificado](#visualización-del-certificado)
    - [Errores al Conectar](#errores-al-conectar)
21. [Subir Cambios a GitHub](#subir-cambios-a-github)
22. [Ejemplo de Subida](#ejemplo-de-subida)
23. [Clonar un Repositorio](#clonar-un-repositorio)
24. [Fork y Pull Request](#fork-y-pull-request)
25. [Issue: Reportar un Error](#issue-reportar-un-error)
26. [Herramientas Gráficas](#herramientas-gráficas)
27. [Flujo de Trabajo con Git Flow](#flujo-de-trabajo-con-git-flow)
28. [GitHub Pages y Actions](#github-pages-y-actions)
29. [Guía rápida para crear un proyecto y subirlo a GIT](#guía-rápida-para-crear-un-proyecto-y-subirlo-a-git)
30. [Atajos](#atajos)
## Configuración Inicial

```sh
mkdir HelloGit
cd HelloGit
code .  # Abre VS Code
```

Configurar Git:

```sh
git config --global user.name "Xavi"
git config --global user.email "xavirambla@yahoo.es"
```

## Crear un Repositorio Git

```sh
mkdir helloGit
cd helloGit
git init  # Inicializar un repositorio Git local
```

## Ramas en Git

```sh
git branch -m main  # Cambiar el nombre de la rama principal de 'master' a 'main'
```

## Git Add y Commit

```sh
git status  # Ver estado del repositorio
git add hellogit.py
git commit -m "Este es mi primer commit"
```

## Historial de Cambios

```sh
git log  # Ver historial de commits
git add hellogit2.py
git commit -m "Este es mi segundo commit"
```

## Revertir Cambios

```sh
git checkout hellogit2.py  # Deshacer cambios en un archivo
git reset  # Volver al último commit o fotografia
```
## Visualizaciones de logs
```sh
git log --graph
git log --graph --pretty=oneline
git log --graph --decorate --all --oneline
```

## Alias en Git
creamos un alias para ejecutar la linea rápidamente.
```sh
git config --global alias.tree "log --graph --decorate --all --oneline"     
git tree  # Ejecutar alias
```

## Gitignore
creación de un fichero fichero .gitignore
```sh
echo "**/config.ini" > .gitignore
git add .gitignore
git commit -m "Añadimos el gitignore"
```

## Comparación de Cambios
Ver diferencias con el último commit
```sh
git diff  
```

## Desplazamiento entre Commits

```sh
git checkout hellogit.py  # Volver al estado inicial
git checkout c528bc0fdf04631f8d0431db4057dc970d1f6edd  # Moverse a un commit específico
git checkout HEAD  # Volver al último commit
```

## Reset en Git

```sh
git reset  # Descartar cambios
git reset --hard  # Eliminar commits irreversiblemente. borra las ramas  y ya no se pueden visualizar
git reflog  # Ver historial completo de cambios
```

## Etiquetas (Tags)
Se ponen etiquetas en los puntos importantes de los commits. Ejemplo versiones.
```sh
git tag clase_1
git tag  # Ver etiquetas
git checkout clase_1  # Moverse a un tag
git checkout main  # Volver a la última versión
```
## Eliminación de un commit
Existe la posibilidad de eliminar un commit, pero no es recomendable su uso
```sh
git revert              
```
## Trabajar con Ramas

```sh
git branch login  # Crear una nueva rama
git switch login  # Cambiar a la rama login
```

### Fusionar Ramas
Pasar todo lo del main a mi rama Login
```sh
git switch login
git merge main  # Fusionar main en login
```

### Manejo de Conflictos
hago un cambio en la rama login
commit del cambio
y vuelvo al head.

hago un cambio sobre el mismo fichero. y lo commit
git switch login
hago un cambio sobre el mismo fichero. y lo commit
```sh
git merge main  # Puede generar conflictos
git add .
git commit  # Resolver conflictos y hacer commit
```
se corrige el conflicto y desaparece el problema.
## Git Stash
Guarda los cambios temporalmente en una especie de memoria temporal. Es para guardar cosas para volver después a ese flujo de trabajo sin necessidad de hacer commits.
```sh
git switch main     / / no me deja moverme pq he ehcho un cambio y no lo he subido pq todavía no me funciona
git stash  # Guardar cambios temporalmente
git stash list  # Ver lista de stashes
git switch main
git switch login
git stash pop  # Restaurar cambios guardados
git stash drop  # Borrar stash
```

## Integración de Cambios

```sh
git switch main
git diff login  # Ver diferencias entre ramas
git merge login  # Fusionar cambios en main
git checkout main               // nos vamos a la última fotografia valida (igual es redundante)
```

## Eliminar Ramas

```sh
git branch -d login  # Eliminar rama
git branch  # Ver ramas
git reflog  # Ver historial de commits
```

## Configuración de GitHub
Subir los cambios en un servidor remoto, ejemplo github.
* Repositorio: es una carpeta donde tenemos el código de un proyecto
* Stars: es marcar como favoritos

### Configuración de GitHub en Windows
Acceder al powershell como administrador
creo una carpeta .ssh para guardar todos los certificados sino existe.
Creamos el certificado
```sh
ssh-keygen -t ed25519 -C "xavirambla@yahoo.es"
ssh-add ~/.ssh/id_rsa_github_xavirambla
```
#### Visualizamos el certificado en nuestro sistema
```sh
ssh -T git@github.com  # Probar conexión con GitHub
```
#### No funciona
Debemos encender el agente 
```sh
Get-WindowsCapability -Online | Where-Object {$_.Name -like 'OpenSSH.Client*'}    # nos dice si tenemos open sssh instalado
Set-Service -Name ssh-agent -StartupType Automatic    # habilitar el servicio ssh
Start-Service ssh-agent      # arrancamos el servicio ssh
```
o manualmente
```sh
Get-Service ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent
```

Ahora toca añadir el certificado al agente
```sh
ssh-add ~/.ssh/id_rsa_github_xavirambla
ssh-add c:/Users/casa/.ssh/id_rsa_github_xavirambla    // hemos añadido la entidad 
```
#### Visualizamos el certificado en nuestro sistema
```sh
ssh -T git@github.com  # Probar conexión con GitHub
```

#### Configuración de config para automatizarlo
Para no tener que hacerlo cada vez, podemos crear un fichero config dentro de la carpeta .ssh para automatizar varias cosas y no tener que repetirlas

Contenido del fichero config
```sh
Host github.com
  AddKeysToAgent yes
#  UseKeychain yes   # esto provoca que nos de errores
  IdentityFile ~/.ssh/id_rsa_github_xavirambla

```

#### Comprobación que la clave se ha introducido
```sh
ssh-add -l               // comprobar que la clave se ha introducido correctamente
```

### Vamos a Github.com
Cogemos el contenido del fichero .pub (clave pública)
[X] Vamos github
[ ] Clickamos sobre nuestro usuario
[ ] Vamos a settings
[ ] Acceder a SSH and GPG Keys
[ ] Click en New SSH Key.
[ ] Pegamos la clave pública
Ejemplo: ssh-ed25519 ABAEC5ZzaD4lZDI1NTE2AbcAIPovs-83Ub635XrDxuShjy1BXPyWdcleIj77xDgYOIjj xavirambla@yahoo.es

### Comprobamos conexión con  Github.com
```sh
ssh -T git@github.com  # Probar conexión con GitHub
```
ahora nos dirá que si estamos autenticados en github pero no tenemos acceso al shell   (Es ok)

#### Errores al conectar

Podemos cambiar la conexión a https pero no es recomendable pq nos pedirá autenticación cada vez.
```sh
git remote set-url origin https://github.com/xavirambla/hello-git.git
git remote set-url origin git@github.com:xavirambla/hello-git.git
```



## Subir Cambios a GitHub
Conectamos nuestra carpeta con el repositorio y subimos los cambios
```sh
git remote add origin git@github.com:xavirambla/hello-git.git
git push -u origin main
```

## Ejemplo de subida
* Añadimos un readme al proyecto
* hacemos un add
* hacemos un commit
* git push     # y no me deja subir pq no estamos actualizados

descargamos en local el historial de cambios,   no descargamos los cambios
```sh
git fetch
```

descargamos en local el historial de cambios,   y descargamos los cambios
```sh
git pull
```

Nos pide configurar como tratará los gitpulls. y nos descarga los cambios


## Clonar un Repositorio
Creamos una nueva carpeta llamada hellogit2 y entramos en ella
```sh
git clone git@github.com:xavirambla/hello-git.git
```
Ahora tenemos dos carpetas distintas con el mismo repositorio.


## Fork y Pull Request
Queremos interactuar con el repositorio de la comunidad o de un desoconocido.
Creamos una nueva carpeta.
```sh
git clone git@github.com:mouredev/hello-git.git
git push  # Falla porque no tenemos permisos
```

Para contribuir:

1. Hacer un fork en GitHub.
2. Clonar el fork. (con un clone)
3. Hacer cambios y subirlos.  ( sube a mi repositorio personal, no a mouredev)

Promocionar a mouredev
1. ir a github y pulsar 'Sync fork'  para sincronizar mi repositorio con el original. Es un merge
2. 'Contribute' -> **open pull request**   Crea una pull request, para pedir su inclusión al repositorio original

Ahora a mouredev, le sale que tiene una pull request , la revisa y puede aceptarla o no .  'Approve' y añadir comments.
'Merge pull request'   -> mouredev hace el merge y los juntas.

## Issue
Se publica la detección de un error al propietario para su revisión.



## Herramientas Gráficas

- **GitHub Desktop**
- **GitKraken**

## Flujo de Trabajo con Git Flow
Crear un flujo estandarizado de trabajo usando la metodologia git Flow


![Descripción de la imagen](https://miro.medium.com/v2/resize:fit:720/format:webp/1*3-0EDzE63S_UZx2KbIz_dg.png)

Main es producción
develop desarrollo

```sh
git flow init  # Iniciar proyecto con Git Flow
# ya me pone en la rama develop
git flow feature start auth  # Crear una feature

# hago cambios
git add .
git commit -m "Añadiendo autenticación"
git flow feature finish auth  # Fusionar cambios en develop
# me borra la rama, me pone los cambios en develop y me pone en la rama develop

git flow release start 1.0  # Crear una release
git flow release finish 1.0  # Fusionar en main y eliminar rama release
```

## GitHub Pages y Actions

- **GitHub Pages** permite publicar proyectos como sitios web.
- **GitHub Actions** automatiza pruebas, builds y despliegues.



# Guía rápida para crear un proyecto y subirlo a GIT
Entrar en la carpeta donde se encuentra el proyecto

```sh
git init
git branch -m main
git add .
git commit -m "First version"
git config --global alias.tree "log --graph --decorate --all --oneline"
git tree
git remote add origin git@github.com:xavirambla/tutoriales.git
git pull origin main --rebase
git push origin main
```

Ya estamos sincronizados, creamos ramas y a trabajar

```sh
git branch cambios
git switch cambios

```

Para subir un cambio a main
```sh
git add .
git commit -m "cambios"
git push origin git


```
y hacemos el pull request para enchufar los cambios a main

Descargar cambios a main

Para subir un cambio a main
```sh
git switch main
git pull origin main
```

# Atajos

Ver en VSCODE el markdown visualmente  ***Control+Shift+v***