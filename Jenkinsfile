pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps{
            checkout([$class: 'GitSCM',
            branches: [[name: '*/main']],
            userRemoteConfigs: [[url: 'https://github.com/anas1243/Deploy-python-redis-app-on-GKE-using-jenkins']]])
        }
        }
        stage('Dockerize The Web App') {
            environment {
                SERVICE_CREDS = credentials('docker_cred')
            }
            steps {
                
                sh "docker build -t anas1243/python-redis-app  -f App/Dockerfile ." 
                sh "docker login -u $SERVICE_CREDS_USR -p $SERVICE_CREDS_PSW"
                sh "docker push anas1243/python-redis-app"
                    
            }
        }
        stage('Deploy The Web App') {
        
            steps {
                
                sh "kubectl create ns prod"
                sh "kubectl apply -f Kubernetes/webApplication --recursive -n prod"
                    
            }
        }
    }
    post {
        success {
            echo "wallah w 3mloha el regala"
        }
    }
}