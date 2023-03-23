# kubernetes

https://github.com/arnaudlef/kubernetes


1. Installer Kind et Kubect

```
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.17.0/kind-linux-amd64
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

2. Pod Nginx

a. Héberger un premier Pod Nginx

Appliquer la configuration du fichier : kubectl apply -f nginx-pod.yaml
Constater la création du pod : kubectl get pods

b. A l’aide de la commande kubectl port-forward et d’un navigateur accéder à la page par défaut de votre pod Nginx
```
kubectl port-forward pod-nginx 80:8080
```

3. Connexion entre plusieurs Pods

a. A l’image du TP 1 sur Docker (question 7 et 8), héberger un Pod phpmyadmin et mysql, cette fois-ci en utilisant minikube

Installer minikube : 
```
	curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
	sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
Ajouter le groupe docker et l'utilisateur au groupe :
```
	sudo groupadd docker
	sudo usermod -aG docker arnal
```

Lancer minikube : minikube start
Appliquer la config de phpmyadmin : kubectl apply -f phpmyadmin.yml
Appliquer la config de mysql : kubectl apply -f mysql.yml

b. Créer un service associé au Pod mysql

Voir fichiers

c. Connecter phpmyadmin avec le Service mysql et vérifier que vous pouvez administrer cette base de données

Voir fichiers

d. Avec la commande kubectl-port forward, vérifier que phpmyadmin arrive à contacter et administrer votre base de données mysql
