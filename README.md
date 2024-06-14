# Práctica de Volúmenes Persistentes en Kubernetes con NGINX
## Descripción
Esta práctica se enfoca en la creación y administración de volúmenes persistentes en Kubernetes, utilizando un contenedor NGINX. A través de este ejercicio, aprenderás cómo definir y utilizar PersistentVolumes (PV) y PersistentVolumeClaims (PVC) para almacenar datos de manera persistente en un clúster de Kubernetes. Además, se incluye una guía para verificar la correcta configuración y almacenamiento de los datos.
## Archivos y Configuración
1. Definición del Pod
El archivo pv-pod.yaml contiene la definición del Pod que utiliza un volumen persistente.
## Pasos para la Implementación
1. Aplicar los Archivos de Configuración:

Aplica los archivos de configuración para crear el Pod, el PersistentVolume y el PersistentVolumeClaim.
```
kubectl apply -f .\pv-pod.yaml
```
2. Verificamos los PersistentVolumes
```
kubectl get pv
```
3. Acceder al Minikube y Verificar el volumen
Accede al entorno de Minikube y verifica que el volumen se haya montado correctamente.
```
minikube ssh
sudo su
cd /data/pv0001/
ls -la
```
4. Modificar el Contenido del Volumen:

Agrega un mensaje de prueba al archivo index.html para verificar que el contenido es persistente.
```
echo "mensaje" >> index.html
exit
exit
```
5. Reenviar el Puerto y Acceder a Nginx
Reenvía el puerto 80 del Pod al puerto 80 de tu máquina local para acceder al servidor Nginx:
```
kubectl port-forward task-pv-pod 80:80
```
Abre tu navegador web y accede a http://localhost:80 para ver el mensaje en el archivo index.html.
## Conclusión
Esta práctica muestra cómo configurar y usar PersistentVolumes y PersistentVolumeClaims en Kubernetes, proporcionando almacenamiento persistente para aplicaciones que lo requieran. Utilizamos un contenedor Nginx como ejemplo para demostrar cómo se puede montar un volumen persistente y servir contenido desde él.
