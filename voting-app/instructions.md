# Voting App Instructions

To start up the kubernetes cluster, run:

```
kubectl apply -f worker-app-deploy.yaml
kubectl apply -f voting-app-deploy.yaml
kubectl apply -f voting-app-service.yaml
kubectl apply -f result-app-deploy.yaml
kubectl apply -f result-app-service.yaml
kubectl apply -f redis-deploy.yaml
kubectl apply -f redis-service.yaml
kubectl apply -f postgres-deploy.yaml
kubectl apply -f postgres-service.yaml

```

To remove all the deployments and services, run:

```
kubectl delete deployment worker-app-deploy
kubectl delete deployment voting-app-deploy
kubectl delete service voting-service
kubectl delete deployment result-app-deploy
kubectl delete service result-service
kubectl delete deployment redis-deploy
kubectl delete service redis
kubectl delete deployment postgres-deploy
kubectl delete service db

```