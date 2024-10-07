#################################################################
# INSTALLATIONS
#################################################################

-------------------------------------------------------# LOCAL INSTALLATIONS # ------------------------------------------------

1. KIND INSTALLATION ON WINDOWS
Key Page: https://kind.sigs.k8s.io/
          https://kind.sigs.k8s.io/docs/user/quick-start#installation


    $ curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.24.0/kind-windows-amd64

- Move kind-windows-amd64.exe to C:\kind\kind.exe
- SET Path = C:\kind

2. KUBERENETES CLUSTER ON LOCAL MACHINE USING KIND:)
    $ kind create cluster --name maink8scluster 

3. KUBECTL INSTALLATION ON WINDOWS
    $ curl.exe -LO "https://dl.k8s.io/release/v1.31.0/bin/windows/amd64/kubectl.exe"

- Move kubectl.exe to C:\kind\kubectl.exe
- SET Path = C:\kubectl
    $ kubectl version

4. KUBERNETS COMMANDS
    $ kind get clusters

    $ kubectl get nodes
    $ kubectl get pods
    $ kubectl get deploy
    $ kubectl describe deployment myapp-sb-deployment-by-kumar

    $ kubectl apply -f mainfest/myapp-sb-deployment.yaml
    $ kubectl delete -f mainfest/myapp-sb-deployment.yaml

    $ kubectl exec --stdin --tty my-pod -- /bin/sh

# Port Forwarding
    $ kubectl port-forward svc/myapp-sb-service-by-kumar 9090:9090

# ipconfig /all


------------------------------------------------------# AWS CLOUD #-------------------------------------------------------------
# SSH CONNECT TO MAIN K8S INSTANCE
1. ssh -i "k8s.pem" ubuntu@ec2-3-143-147-197.us-east-2.compute.amazonaws.com

2. After connecting to Machince,
   $ sudo su
   $ cd
   $ mkdir <<name>>
   $ cd <<name>>

3. Version Control System - GIT
    Key page: https://git-scm.com/download/linux

    $ sudo apt-get install git -y
    $ git --version

4. Build Tool - Maven and JDK - Java
   $ sudo apt-get update
   $ sudo apt-get install openjdk-17-jdk -y
   $ ls /usr/lib/jvm/
   $ nano ~/.bashrc
   ```bash
      export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
      export PATH=$JAVA_HOME/bin:$PATH
   ```
   $ source ~/.bashrc
   $ echo $JAVA_HOME
   $ which java
   $ sudo apt-get install maven -y
   $ mvn -version

5. Programmatically Create Resources in AWS : (Commands) - AWS Command Line Interface
   Key Pages: https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#cliv2-linux-install

   $ aws --version
   $ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   $ apt-get install unzip -y
   $ unzip awscliv2.zip
   $ sudo ./aws/install

6. FOR AWS EC2 DOCKER INSTALLATION
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

7. Push Images to AWS ECR
    aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 932589472370.dkr.ecr.us-east-2.amazonaws.com
    docker build -t myapp-sb .

    docker tag myapp-sb:latest 932589472370.dkr.ecr.us-east-2.amazonaws.com/myapp-sb:latest
    docker push myapp-sb:latest 932589472370.dkr.ecr.us-east-2.amazonaws.com/myapp-sb:latest

8. KUBECTL INSTALLATION ON AWS UBUNTU LINUX MACHINE
    $ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    $ sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

9. EKSCTL INSTALLATION
   $ curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   $ sudo mv /tmp/eksctl /usr/local/bin
   $ eksctl version
   $ eksctl create cluster --name sigmaEKS-Cluster --region us-east-2 --nodegroup-name sigmaEKS-Cluster-NG --node-type t2.micro --nodes 2 --nodes-min 2 --nodes-max 5 --ssh-access --ssh-public-key kp --managed