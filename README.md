# configs-cadavre-exquis
Utilisation de minukube : 
- installer minikube 
- démarrer un cluster minikube `minikube start`

Ensuite on peut appliquer les configurations : 

```
kubectl apply -f ./Deployements
kubectl apply -f ./Services
```

## accès avec minikube 
```
minikube service dispatcher --url
```

## rollout
## composition des deployments 
### dispatcher 

