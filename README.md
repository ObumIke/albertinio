## KUBERNETES - Easy way to go
## Run your VMware
- VMware or through SSH can be used.
- sudo su [be on the root]
- apt-get update [run update on your vmware]
- apt-get upgrade [upgrade your Vmware]
## VIRTUALBOX - Install
- sudo apt install virtualbox virtualbox-dkms virtualbox-qt virtualbox-ext-pack [install virtualbox]
## DOCKER - Install
- Step 1: # Add Docker's official GPG key: sudo apt-get update sudo apt-get install ca-certificates curl gnupg sudo install -m 0755 -d /etc/apt/keyrings curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg sudo chmod a+r /etc/apt/keyrings/docker.gpg # Add the repository to Apt sources: echo \ "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \ "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \ sudo tee /etc/apt/sources.list.d/docker.list > /dev/null sudo apt-get update
- Step 2: sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
- docker - - version [confirm the Docker version]
- systemctl enable docker [enable Docker]
- systemctl start docker [start the Docker]
- systemctl status docker [confirm Docker status]
- sudo usermod -aG docker $USER && newgrp docker
## MINIKUBE - Download and Install
- wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 
chmod +x minikube-linux-amd64 
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
- minikube version [confirm minikube version]
## KUBECTL ON UBUNTU
- curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
- chmod +x ./kubectl [change mode]
- sudo mv ./kubectl /usr/local/bin/kubectl
- Verify kubectl [to verify your kubernetes]
- kubectl version -o json --client [confirm kubenertes version]
- minikube start --driver=docker [start the kubernetes]
- sudo usermod -aG docker $USER && newgrp docker
- kubectl get nodes
- kubectl create deployment obumneme –image=nginx [you need to specify the name of your deployment and image [ubuntu, nginx etc]
- minikube dashboard [confirm your deployment. deployment will be launched on your default browser. Check your browser]
- minikube addons enable metric-server
- Kubectl expose deployment obumneme --type=NodePort --port=8080 [enable port 8080]
- Kubectl get service
- Kubectl describe service
- Kubectl describe deployment
- Kubectl delete service obumneme
- Kubectl delete deployment obumneme
- Minikube stop
## PODS - KUBERNETES
- mkdir obumk8s-pods
- cd obumk8s-pods
- minikube start --driver=docker
- kubectl run obumk8s-pods --image=redis
- kubectl get pods
- kubectl get pod obumk8s-pods -o yaml
- kubectl describe pod obumk8s-pods
- kubectl run albertinok8s-pods --image=nginx --dry-run=client -o yaml > obum.yaml [create another pods as sidecar]
- cat obum.yaml
- vim obum.yaml [use vim to edit the yaml file. create another image and file name for a sidecar] :wq to save
- kubectl apply -f obum.yaml
## PODS DEPLOYMENT - KUBERNETES
- kubectl create deployment obumk8s-dep --image=ubuntu
- kubectl edit deployment obumk8s-dep
- kubectl get deployment obumk8s-dep
- kubectl delete deployment obumk8s-dep
- kubectl create depolyment albertinok8s-dep --image=nginx
- kubectl scale deployment albertinok8s-dep --replicas=12
- minikube dashboard [confirm your deployment. deployment will be launched on your default browser. Check your browser]
- minikube addons enable metric-server [run minikube sddons]
- minikube dashboard [confirm your deployment. deployment will be launched on your default browser. Check your browser]
- minikube stop [this can be used for instant shutdown: sudo shutdown -h now]

