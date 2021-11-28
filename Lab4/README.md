kustomization.yaml
beschreibt die Anpassung von Kubernetes Konfugurationen. Hier definiert es einen secret generator, mit dem ein objekt generiert wird, dass sensible daten beinhaltet wie zb Passwörter. Weiters kann man noch Resourcen angeben, in diesem Fall Wordpress und MySQL.

mysql-deployment.yaml
Beschreibt eine Instanz einer MySQL Deployment. Weiters wurde hier ein PersistentVolume angelegt welches an "/var/lib/mysql" festlegt.

wordpress-deployment.yaml
Selbes Prinzip wie bei mysql, wobei das PersistentVolume an "/var/www/html" gebunden ist. Wordpress greift auf die Datenbank per Service zu.


Schritte:
az group create --name myResourceGroup --location eastus

az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 1 --enable-addons monitoring --generate-ssh-keys

az aks get-credentials --resource-group myResourceGroup --name myAKSCluster

kubectl apply -k ./
The kustomization.yaml contains all the resources for deploying a WordPress site and a MySQL database.

kubectl get services wordpress
coyp address, port 80, enter in browser

kubectl delete -k ./
delete your Secret, Deployments, Services and PersistentVolumeClaims: