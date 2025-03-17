# StudentApp
Application web conteneurisée avec Docker et orchestrée avec Kubernetes, composée de trois pods (frontend, backend, base de données) interconnectés pour gérer des étudiants.  

---

Objectif du projet  
Développer et déployer une application web en utilisant Docker et Kubernetes, tout en assurant l’orchestration des conteneurs et la gestion de la base de données MySQL.   

---

Fonctionnalités  
- Formulaire d'inscription : Ajout d’étudiants via un formulaire interactif.  
- Page d'accueil : Liste des étudiants inscrits.  
- Gestion des étudiants : Modification et suppression des inscriptions.  

---

1. Installation et déploiement  
  Prérequis  
- [Docker](https://www.docker.com/get-started)  
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)  
- [Kubectl](https://kubernetes.io/docs/tasks/tools/)  
- [Node.js & npm](https://nodejs.org/)  

---

2. Mise en place du projet  
Backend (Express.js)  
cd server   
npm init -y   
npm install express cors body-parser   
npm install -g nodemon   
npm run dev   

---

Frontend (React + Vite)   
cd client   
npm create vite@latest . -- --template react   
npm install   
npm run dev   

---

3. Configuration et exécution de Docker & Kubernetes   
Démarrer Minikube:   
minikube start   
eval $(minikube docker-env)   

---
---

Lancer Docker Compose:   
docker-compose up --build -d   

---

4. Déploiement sur Kubernetes   
Déploiement de la base de données:   
kubectl apply -f mysql-secret.yaml   
kubectl apply -f mysql-configmap-script.yaml   
kubectl apply -f mysql-pvc.yaml   
kubectl apply -f mysql-deployment.yaml   

---

Déploiement du backend et frontend:   
kubectl apply -f backend-deployment.yaml   
kubectl apply -f frontend-deployment.yaml   

---

Déploiement des services:   
kubectl apply -f mysql-service.yaml   
kubectl apply -f backend-service.yaml   
kubectl apply -f frontend-service.yaml   

---
---

5. Vérifications et tests:   
Vérifier le bon fonctionnement des pods et services:   
kubectl get pods   
kubectl get svc   
kubectl get pvc   

---

Tester la connexion à la base de données:   
kubectl exec -it <mysql-pod> -- mysql -u root -p   

---

Vérifier la communication entre les services:   
kubectl exec -it <frontend-pod> -- sh -c "curl http://backend-service:5000"   

---

Accéder à l'application:   
minikube service frontend-service   
ou    
http://localhost:80   

---
---

6. Suivi et monitoring   
kubectl get services   
minikube dashboard   

---

Rafael Barreto Pannetier - Étudiant ingénieur en informatique.




