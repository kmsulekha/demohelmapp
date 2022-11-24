# Install Minikube

## install docker

    apt-get install docker.io
    systemctl start docker
    
## install kubectl

    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
    kubectl version --client
    
  
## install minikube

    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
    minikube version
    
## install Helm

    curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
    chmod 700 get_helm.sh
    ./get_helm.sh
  
## start minikube 

    minikube start --force
    minikube status
    
## build docker image

    cd  /oot/python-flask-docker
    docker build -t <docker hub username>/sample-app .
    
## push docker image to docker hub

    docker login
    docker push <docker hub username>/sample-app
    
# Deploy Application 

## clone the repo

    git clone https://github.com/kmsulekha/demohelmapp.git
    cd demohelmapp
    ls
    
 ## kubectl command to create namespace
    
    kubectl create ns sample-app 
    kubectl get ns
 
## deploy helm chart using helm

    helm install sample-app  sample-app  --namespace sample-app 
    
## helm command to list all the deployed helm chart

    helm list
    helm list -n sample-app 
    
## kubectl command to check deployement

    kubectl get deployment -n sample-app 
    
## kubectl command to check pods

    kubectl get pods -n sample-app 
    
## kubectl command to check services

    kubectl get svc -n sample-app 
    
## kubectl command to check node 

    kubectl get nodes -o wide
    
 -- copy node ip and service node port
 
 ## access the application using curl
 
    curl <node ip>:<nodeport>
    
 ## kubectl command to check all the created resources in a particular namespace
 
    kubectl get all -n sample-app 
    
## helm command to upgrade application

    helm upgrade <release name> <chart name> -n sample-app 
    
## helm command to uninstall application

    helm uninstall <release name>
    
    
