#################################################################
# INSTALLATIONS
#################################################################

# 1. KIND INSTALLATION
Key Page: https://kind.sigs.k8s.io/
          https://kind.sigs.k8s.io/docs/user/quick-start#installation


$ curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.24.0/kind-windows-amd64

- Move kind-windows-amd64.exe to C:\kind\kind.exe
- SET Path = C:\kind



# 2. KUBERENETES CLUSTER ON LOCAL MACHINE USING KIND:)
$ kind create cluster --name maink8scluster 


# 3. KUBECTL INSTALLATION ON WINDOWS
 $ curl.exe -LO "https://dl.k8s.io/release/v1.31.0/bin/windows/amd64/kubectl.exe"

- Move kubectl.exe to C:\kind\kubectl.exe
- SET Path = C:\kubectl
 $ kubectl version


# 4. FOR AWS EC2 DOCKER INSTALLATION
    # For Ubuntu
    sudo su
    cd
    apt-get update -y
    apt-get install docker.io -y
    docker pull ssadcloud/myapp-sb:latest
    docker run ssadcloud/myapp-sb:latest


    # For Amazon Linux
    sudo su
    cd
    yum install docker -y
    docker pull ssadcloud/myapp-sb:latest
    docker run ssadcloud/myapp-sb:latest

# KUBERNETS COMMANDS
kind get clusters


kubectl get nodes
kubectl get pods

kubectl get deploy
kubectl describe deployment myapp-sb-deployment-by-kumar

kubectl apply -f mainfest/myapp-sb-deployment.yaml
kubectl delete -f mainfest/myapp-sb-deployment.yaml

kubectl exec --stdin --tty my-pod -- /bin/sh

# Port Forwarding
kubectl port-forward svc/myapp-sb-service-by-kumar 9090:9090

# ipconfig /all