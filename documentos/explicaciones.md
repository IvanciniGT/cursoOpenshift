
OPENSHIFT (Controlplane: POD: Consola WEB-POD, OS-API)
-------
KUBE-API (POD) que se ejecuta dentro de 1 maquina del cluster (MAESTRO)
---V---
KUBELET & KUBE-PROXY (RED entre todas las máquinas del cluster)
---V---
DOCKERD (RED en 1 maquina)
-------
SO
-------
HIERRO






1 Máquina: 10 máquinas
docker          10 veces docker, con parametros diferentes....


Nodo1
Nodo2
    MariaDB  <<<< descargar la imagen
                    docker pull mariadb
                        ---> crear un contenedor
                            docker create 
                                --> arrancarlo
                                    docker start
                    docker run --name mitomcat tomcat 
                                    -- gestion de los puertos y redes
Nodo3
.....

Nodo10

Contenedores: MariaDB





---------------------------------
POD:
Conjunto de contenedores que:
    - Se ejecutan dentro de un mismo nodo
    - Comparten configuración de red <- Comparten IP privada en el cluster
    - Volumenes <- Pueden compartir volumenes

Mínima unidad de trabajo dentro de un Cluster de OS/Kb

TODA DEFINICION de un objeto que quiera crear en Kubernetes se hace dentro de un fichero YAML
kubectl apply -f <RUTA DEL FICHERO>



Statefulset
ReplicaSet
    POD
        Varios Contenedores
        
        
        
        
        
Filebeat -> Va leyendo en tiempo real lineas del fichero de log y las manda a una BD Externa (ElasticSearch)
        
TOMCAT | JBOSS | WEBLOGIC | LIBERTY | WEBSPHERE | WILDFLY: Serv. de aplicaciones JAVA        
    Aplicación (Reserva de vacaciones y dias libres + ausencias justificadas al trabajo ---BAJAS--- ITNOW)     <<<<< VALOR
    Tipo de aplicación: Aplicación WEB -> Qué implica?? Comunicación va a realizarse mediante protocolo? HTTP(s)
        2 replicas de un POD: Conjunto de contenedores
            Contenedor 1: Tomcat (log) + MiApp (logapp)   >>>> MariaDB
                -> Docker (FS ->  C1:/ === HOST:/var/contenedor1  )
                -> Volumen logs y lo monte: C1:/logs (.//log & logapp ) ----> HOST:/var/logs
                -> Volumen ficheros temporales y lo monte: C1:/datos  ----> ALMACENAMIENTO EXTERNO: (redundante) 
            Contenedor 2: FileBeat  (monitorizar el fichero de log del tomcat + Moniotizar el fichero de log de mi app
                -> Docker (FS -> C2:/ === HOST:/var/contenedor2)
                -> Volumen logs y lo monte: C2:/mislogs (.//log & logapp ) ----> HOST:/var/logs
                -> Volumen ficheros temporales y lo monte: C1:/datos  ----> ALMACENAMIENTO EXTERNO: (redundante) 
            Volumen
                logs ===>> /var/logs
PVClaim -> StorageClass -> PV

Cluster Kuber/OpS
    Maestro 1
        Plano de Control (PODS)

    Nodo 1                                 Imagen                 Generados dinámicamente tomcat + app
        PodAppVacaciones (copia1)           VVV                                     VVV
            C1: Tomcat+app          |   FS: Local    +   Montado un volumen logs ( LOCAL )
                                    |   CabAlm /datosC1 --->>  /datos  Archivos temporales
            C2: FileBeat            |   FS: Local    +   Montado un volumen logs ( LOCAL )
            
    Nodo 2                                 Imagen                 Generados dinámicamente tomcat + app
        PodAppVacaciones (copia2)           VVV                                     VVV
            C1: Tomcat+app          |   FS: Local    +   Montado un volumen logs ( LOCAL )
                                    |   CabAlm /datosC2 --->>  /datos
            C2: FileBeat            |   FS: Local    +   Montado un volumen logs ( LOCAL )

    Nodo 3 EXPLOSION !!!!!!                  Imagen                 Generados dinámicamente tomcat + app
        --- PodAppVacaciones (copia2)         VVV                                       VVV
            --- C1: Tomcat+app          |   FS: Local    +   Montado un volumen logs ( LOCAL )
                                        |   CabAlm /datosC2 --->>  /datos
            --- C2: FileBeat            |   FS: Local    +   Montado un volumen logs ( LOCAL )
    
StatefulSet
    PodCopia1
        PodCopia2 ------> Maquina 1 
    PodCopia2 ------> Maquina 5
        Todos los volúmenes que tuviera el PorCopia2 de la maquina 1 se montan LOS MISMOS en la máquina 5
    PodCopia3

Deployment <- ReplicaSet
    PodCopia_KAJSJKA
        PodCopia2_asljhdakjhadkj ------> Maquina 1 
    PodCopia2_asljhadkjha ------> Maquina 5
        Todos los volúmenes del nuevo pod PodCopia2_asljhadkjha SE CREAN DE NUEVO EN LA CABINA
    PodCopia3

Cabina de Almacenamiento
    /datosC1
    /datosC2 <<<<<
    /datosC287326874982983
    
    
    
/datos/IDs unicos


Cliente externo: Aplicación ... compras
    Cliente: Ivan----> Nodo1  <<<<<< Mientras el nodo esté disponible, siempre deberia llevarme al mismo nodo.
        

CLuster: Kuberetes/Openshift
    Ingres : Route -> Balanceador (Apache, nginx)
        StickySessions
    Servicio: Balanceador ---> Nodo1
                          ---> Nodo2
    Nodo1 
        Tomcat + nominas (datos en memoria RAM)  >>> MariaDB
    Nodo2                         
        Tomcat + nominas (datos en memoria RAM)  >>> MariaDB
    Nodo3
        Tomcat + nominas (datos en memoria RAM)  >>> MariaDB

BD MAriaDB





NameSpace: Entorno aislado dentro de un cluster
Namespace: desarrollo
Namespace: produccion

Namespace: cliente1
Namespace: cliente2

