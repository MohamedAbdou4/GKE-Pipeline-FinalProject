# GKE-Pipeline-FinalProject

First the tools we used to build this infrastructure

1- Docker

2- Jenkins

3- Kubernetes

---------------------------------------------------------------------------------------------------------------

First we will use the VM as an agent jenkins to run the pipeline


our pipeline will need docker to build and push the image we will use for oue application


and then deploy the application on the cluster using kubectl on different namespace

--------------------------------------------------------------------

        
           a- # install docker
              $ sudo apt-get update
              $ sudo apt-get install docker.io
              $ sudo chmod 666 /var/run/docker.sock
              
           b- #create namespcae for your app 
              $ kubectl create namespace node-app-ns
              
           e- install requierments for jenkins
              $ sudo apt install -y openjdk-11-jdk
              $ ssh-keygen
              $ mkdir jenkins_home #as a jenkins working dir
              $ cat .ssh/id_rsa.pub
              $ vim authorized_key
              # put the puplic key
              # copy your private key 
              
           f- mange nodes and put credentials on jenkins master 
              1- For docker hub
              2- For VM ( use your private key )
            
           g- create your pipeline 
              put the repo link for Jenkinsfile
              build it
     
           h- access your application
              $kubectl get svc -n node-app-ns
              get you external ip for the service

-----------------------------------------------------------------------------------------------------------------
