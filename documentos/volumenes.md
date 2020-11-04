

Volumenes
---------
Locales:
    emptyDir <- Carpeta local en el nodo vacia
    emptyDir <- Carpeta en RAM que se monte como carpeta
    
Volumenes persistentes: No están en el nodo
    - NFS
    - CIS
    - CLOUD

PV <- 200Gi Gibibytes 200 x 1024x1024x1024 bytes  ---> NFS , CLOUD ---> volumen-jenkins

POD: Volumen <- PV Claim

Jenkins
 Volumen datosDelJenkins -> /var/jenkins
            Se obtiene de una Petición de Volumen (PVC): peticion-volumen-jenkins (100Gi)
            ----> volumen-jenkins (200Gi)
            
-----
Kubernetes Generador automatico de Volumenes Persistentes NFS
Openshift    ^^^^
    Deployment (POD)
-----
kind: pvc
metadata:
    name: peticion-volumen-jenkins
spec: TAMAÑO: 100Gi

