# Files
## kustomization.yaml <br />
Beschreibt die Anpassung von Kubernetes Konfugurationen. Hier definiert es einen secret generator, mit dem ein objekt generiert wird, dass sensible daten beinhaltet wie zb Passwörter. Weiters kann man noch Resourcen angeben, in diesem Fall Wordpress und MySQL.

## mysql-deployment.yaml <br />
Beschreibt eine Instanz einer MySQL Deployment. Weiters wurde hier ein PersistentVolume angelegt welches an "/var/lib/mysql" festlegt.

## wordpress-deployment.yaml <br />
Selbes Prinzip wie bei mysql, wobei das PersistentVolume an "/var/www/html" gebunden ist. Wordpress greift auf die Datenbank per Service zu.


# Schritte:
az group create --name myResourceGroup --location eastus  

az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 1 --enable-addons monitoring --generate-ssh-keys

az aks get-credentials --resource-group myResourceGroup --name myAKSCluster

kubectl apply -k ./
![alt text](https://github.com/TheRealDealveloper/Software-Deployment/blob/main/Lab4/Pictures/kube%20apply.png)
*Das kustomization.yaml beinhaltet alle Resourcen für das Deployment von einer WordPress Webseite and einer MySQL Datenbank.*

kubectl get services wordpress
![alt text](https://github.com/TheRealDealveloper/Software-Deployment/blob/main/Lab4/Pictures/kube%20get%20service.png)
*External-IP und Port 80 ergeben die URL (Port 80, weil es in den Resourcen so in der yaml Datei definiert worden ist), und im Browser eingeben*

kubectl delete -k ./
![alt text](https://github.com/TheRealDealveloper/Software-Deployment/blob/main/Lab4/Pictures/kube%20delete.png)
*Zum löschen der Secrets, Deployments, Services und PersistentVolumeClaims:*
