# Comandos GIT

## Sistema de control de versión / Repositorio
Un servicio que permite almacenar todos los ficheros asociados a un proyecto: REPOSITORIO
Además registra todos los cambios que se van realizando sobre los ficheros.
GIT: Es un sistema de control de versión. Es como un motor/protocolo de sistema de control de versión.
Distribuciones de GIT: GITHUB, GITLAB, BITBUCKET

## GIT es un sistema de control de versión DISTRIBUIDO:
No hay un repositorio central al que TENGA que conectarme para trabajar.
En su lugar dentro de GIT existe el concepto de REPOSITORIO REMOTO... y git permite tener MUCHOS REPOSITORIOS REMOTOS.
Cuando una persona está trabajando con un proyecto, tiene una copia de TODO el proyecto, incluyendo el histórico de cambios.

## Entornos de trabajo:

    CARPETA LOCAL      <>      AREA DE STAGING        <>    COPIA LOCAL REPO          <>      REPO REMOTO
                                  (temporal)
## Comando GIT
Nos permite controlar y ejecutar todas las operaciones del repositorio

### Crear un repositorio en LOCAL:
Genera area de staging y me prara la carpeta de trabajo
> git init 

### Añadir ficheros al area de staging
Iniciar el seguimiento de un fichero
> git add <nombre del fichero>
> git add *
> git add logs/*

### Confirmar cambios en el repositorio LOCAL
> git commit -m 'MENSAJE LOG'

### Establecer el usuario a NOMBRE del que se anotarán los cambios
> git config --global user.name "Ivan"
> git config --global user.email ivan.osuna.ayuste@gmail.com

### Estado actual de la carpeta en la que trabajamos
> git status -s

### Diferencias entre lo que tengo en staging y en la carpeta
> git diff

### Revertir un cambio en la carpeta (REPO LOCAL >>> CARPETA)
> git checkout

### Para añadir un repo remoto
> git remote add origin https://github.com/IvanciniGT/conceptosGIT
                 <nombre identificando al repo remoto> === origin

### Para enviar al repo remoto:
> git push -u origin master

### Para copiar un remo remoto en local:
> git clone https://github.com/IvanciniGT/conceptosGIT <NOMBRE DE LA CARPETA LOCAL>

### Para traerme cosas del repo:
> git fetch (Las trae a mi repo local)
> git pull (las trae a mi repo local, staging y carpeta local)

## Concepto de RAMA: branch
Versión del conjunto de ficheros del proyecto

Proyecto: Crear unos recursos en Openshift:
    - Crear una route (+- equivalente a ingress kubernetes)     |   Crearlos manualmente desde la consola WEB (RUINA)    
    - Configmaps                                                |
    - Secrets                                                   |   Tener las definiciones en ficheros YAML
    - ...                                                       |
    Proyecto.v1 <<<<< DONE
        >>>> Producción
    Proyecto.v2 <<<<< PROGRESS
        Tenemos todo en pinzas
            - Modificando los configmaps
            - Añadiendo nuevos configmaps
    
    Producción: Quiero unos parametros dentro un configmap
    
    Por defecto, todo proyecto de GIT tiene una rama principal llamada MASTER
    En github hace 1 mes han cambiado el nombre de la rama master - slave
                                                            main  - worker

    V1 >>>>> (+) >>>>>>>>>>>>>(+)(+)>>>>>>(+)>>>>>>>>> (PRODUCCION)>>>>>>>>>(+)> (PRODUCCION)
                                                                             V
    V2                                                          >>> (+) >(+)(+)>>>>(+)>>>>>>>>>
                                                                            ^ (Hay que cambiar un config map de prod)

### Para crear una rama: 
> git checkout -b <nombre rama>

### Para ir a una rama: 
> git checkout <nombre rama>

### Para fusionar una rama con otra:
> git merge <nombre rama>
                                                    