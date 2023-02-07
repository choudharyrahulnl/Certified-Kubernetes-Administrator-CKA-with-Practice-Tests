# Certified-Kubernetes-Administrator-CKA-with-Practice-Tests

# Namespace
kubectl create namespace cka
kubectl delete namespace cka

# Pod
kubectl create -f nginx-pod.yaml
kubectl delete -f nginx-pod.yaml
kubectl run nginx --image=nginx
# Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)
kubectl run nginx --image=nginx --dry-run=client -o yaml -n cka

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

# Service
kubectl create -f nginx-nodeport-service.yaml ( access http://localhost:30008/)
kubectl delete -f nginx-nodeport-service.yaml