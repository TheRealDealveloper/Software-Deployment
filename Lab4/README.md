kustomization.yaml
beschreibt die Anpassung von Kubernetes Konfugurationen. Hier definiert es einen secret generator, mit dem ein objekt generiert wird, dass sensible daten beinhaltet wie zb Passwörter. Weiters kann man noch Resourcen angeben, in diesem Fall Wordpress und MySQL.

mysql-deployment.yaml
Beschreibt eine Instanz einer MySQL Deployment. Weiters wurde hier ein PersistentVolume angelegt welches an "/var/lib/mysql" festlegt.

wordpress-deployment.yaml
Selbes Prinzip wie bei mysql, wobei das PersistentVolume an "/var/www/html" gebunden ist. Wordpress greift auf die Datenbank per Service zu.


Schritte:

kubectl apply -k ./
kubectl get services wordpress
