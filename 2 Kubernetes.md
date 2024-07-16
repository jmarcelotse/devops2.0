#######KIND#######
Alias	Command
kicc	kind create cluster
kiccn	kind create cluster --name
kigc	kind get clusters
kidc	kind delete cluster
kidcn	kind delete cluster --name
kidca	kind delete clusters -A
kigk	kind get kubeconfig

#######k3d#######

k3d cluster create (forma simples)

k3d cluster list

k3d cluster create nxt-cluster --servers 3 --agents 3

#######kubectl#######

k3d cluster create nxt-cluster --servers 3 --agents 3

k3d cluster delete nxt-cluster

##############################

kubectl api-resources

criar o deployment.yaml
    kind: Deployment

kubectl apply -f k8s/deployment.yaml

kubectl get pods

criar o service no mesmo manifesto do deployment separando com ---
    kind Service

kubectl apply -f k8s/deployment.yaml

kubectl get svc

kubectl get deployments

kubectl get replicasets

kubectl get pods

kubectl get all

kubectl port-forward pod/postgre-8498dc7858-p4r7g 5432:5432 (teste de conexao)
kubectl port-forward service/postgre 5432:5432

#######Criar uma aplicação Web#######
/home/jmarcelotse/tse/devops2.0/devops4devs-01/src

docker build -t jmarcelotse/devops4devs-news:v1 .

docker image ls

docker push jmarcelotse/devops4devs-news:v1

docker tag  jmarcelotse/devops4devs-news:v1 jmarcelotse/devops4devs-news:latest

docker push jmarcelotse/devops4devs-news:latest

#######Criar o Deployment da aplicação da imagem acima criada e enviada para dockerhub

Vai usar o mesmo manifesto deployment separado por ---
    kind: Deployment

kubectl apply -f k8s/deployment.yaml

kubectl get pods

#######Criar o Service para acessar a aplicação no mesmo yaml separado por ---
    kind: Service

kubectl apply -f k8s/deployment.yaml

kubectl get all

#######Para Acessar aplicação por fora vai ser preciso criar o redicionamento na criação do cluster.

k3d cluster create nxt-cluster --servers 3 --agents 3 -p "30000:30000@loadbalancer"

 kubectl apply -f k8s/deployment.yaml

 kubectl get all

 kubectl rollout history deployment web

 kubectl rollout history undo deployment web