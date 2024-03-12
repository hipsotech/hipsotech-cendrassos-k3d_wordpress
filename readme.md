# "Desplegant wordpress a k8s"

Repositori creat per a la demo live del webmentors del Cendrassos. 👨‍🎓​

### Create cluster ⚓

k3d cluster create wordpress-cluster-demo

### Despleguem la base de dades MySQL

kubectl apply -f ./src/db/01_mysql-pvc.yaml

kubectl apply -f ./src/db/02_mysql-deployment.yaml

kubectl apply -f ./src/db/03_mysql-service.yaml

### Tot seguit desplegarem el Wordpress

kubectl apply -f ./src/wordpress/01_wordpress-pvc.yaml

kubectl apply -f ./src/wordpress/02_wordpress-deployment.yaml

kubectl apply -f ./src/wordpress/03_wordpress-service.yaml

### Ara nomes queda exposar  el servei en un port local

kubectl port-forward service/wordpress 8080:80

### Esborrem el cluster de prova

k3d cluster delete wordpress-cluster-demo