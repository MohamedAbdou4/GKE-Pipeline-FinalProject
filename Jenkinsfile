pipeline {

     
    agent {label "agent-app"}

    stages {
        stage('get code') {
            steps {
                
                git 'https://github.com/MohamedAbdou4/GKE-Pipeline-FinalProject'
            }
        }
        
        stage('CI'){
            steps{
               
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                
                
                sh '''
                    docker build . -f dockerfile -t mohamedabdou4/final-project-node-app-1
                    docker login -u ${USERNAME} -p ${PASSWORD}
                    docker push mohamedabdou4/final-project-node-app-1
                '''
                }
            }   
        }

        stage('CD'){
            steps{
                
                sh ''' 
                    kubectl apply -n node-app-ns -f /home/moabdou4/jenkins_home/app-K8s/node-app-dep.yml
                    kubectl apply -n node-app-ns -f /home/moabdou4/jenkins_home/app-K8s/node-app-svc.yml
                '''
            }
        }
    }
}
