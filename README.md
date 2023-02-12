# Certified-Kubernetes-Administrator-CKA-with-Practice-Tests

# Namespace
kubectl create namespace cka
kubectl delete namespace cka

# Pod
kubectl create -f nginx-pod.yaml
kubectl delete -f nginx-pod.yaml
kubectl run nginx --image=nginx OR kubectl run nginx-pod --image=nginx:alpine
kubectl run custom-nginx --image=nginx
kubectl run httpd --image=httpd:alpine
kubectl run mosquito --image=nginx
kubectl run bee --image=nginx
# Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)
kubectl get po elephant -o yaml > elephant.yaml
kubectl run nginx --image=nginx --dry-run=client -o yaml -n cka
kubectl run redis --image=redis:alpine --dry-run=client -o yaml -n cka

# ReplicaSet
kubectl create -f nginx-replica-set.yaml
kubectl delete -f nginx-replica-set.yaml

# Deployment
kubectl create -f nginx-deployment.yaml
kubectl delete -f nginx-deployment.yaml
kubectl create deployment --image=nginx nginx 
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml -n cka
# Generate Deployment YAML file (-o yaml). Don't create it(--dry-run) with 4 Replicas (--replicas=4)
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml -n cka
kubectl create -f nginx-deployment.yaml
kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml -n cka
kubectl create deployment --image=kodekloud/webapp-color webapp --replicas=3 -o yaml > webapp-deployment.yaml
kubectl create deployment --image=redis redis-deploy --replicas=2 --namespace=dev-ns -o yaml > redis-deployment.yaml
kubectl create deployment --image=nginx blue --replicas=3 -o yaml > blue-deployment.yaml


# Service
kubectl create -f nginx-nodeport-service.yaml ( access http://localhost:30008/)
kubectl delete -f nginx-nodeport-service.yaml
# Create a Service named redis-service of type ClusterIP to expose pod redis on port 6379
kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml
kubectl expose pod custom-nginx --port=8080 --name custom-nginx-service
# This will not use the pods labels as selectors, instead it will assume selectors as app=redis
kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml
# Create a Service named nginx of type NodePort to expose pod nginx's port 80 on port 30080 on the nodes:
kubectl expose pod nginx --type=NodePort --port=80 --name=nginx-service --dry-run=client -o yaml
kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml
kubectl expose pod httpd --type=ClusterIP --port=80 --name=httpd

# Namespace
kubectl create namespace cka
kubectl delete namespace cka

# Change Namespace
kubectl config set-context --current --namespace=cka
kubectl config view --minify | grep namespace:

kubectl config set-context $(kubectl config current-context) --namespace=cka
kubectl config view --minify | grep namespace: