# configs-cadavre-exquis

## ansible deploy
Create some debian VMs with different hostnames, no swap and at least 2vCPU and 2 Go of ram.  
Add the created VMs to the inventory following this schema : 
```ini
<name> ansible_user=root ansible_host=<vm ip> ansible_ssh_private_key_file=<private key file location>
```

Add them to the corresponding groups, example : 
```ini
control ansible_user=root ansible_host=192.168.122.40 ansible_ssh_private_key_file=~/.ssh/id_rsa
worker1 ansible_user=root ansible_host=192.168.122.191 ansible_ssh_private_key_file=~/.ssh/id_rsa


[worker]
worker1

[control]
main
```
Then **change dir to ansible** an run :
```bash
ansible-playbook main.yml 
```
This should create the kubernetes cluster and deploy the app. There should be at least one control.  
If a problem with kubernetes appear, execute `kubeadm reset` on all hosts and redeploy the ansible playbook.  

The service should be accessible on `<control-ip>:30000`

## minikube
Utilisation de minukube : 
- installer minikube 
- démarrer un cluster minikube `minikube start`

Ensuite on peut appliquer les configurations : 

```bash
kubectl apply -f ./Deployements
kubectl apply -f ./Services
```

## accès avec minikube 
```bash
minikube service dispatcher --url
```

