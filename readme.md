# Create cluster
k3d cluster create wordpress-cluster-demo

# Deploy wordpress
kubectl apply -f ./src/db/01_mysql-pv.yaml
kubectl apply -f ./src/db/02_mysql-statefulset.yaml
kubectl apply -f ./src/db/03_mysql-service.yaml

kubectl apply -f ./src/wordpress/01_wordpress-pv.yaml
kubectl apply -f ./src/wordpress/02_wordpress-deployment.yaml
kubectl apply -f ./src/wordpress/03_wordpress-service.yaml

# Expose wordpress service
kubectl port-forward service/wordpress-service 8080:80

# Delete cluster
k3d cluster delete wordpress-cluster-demo