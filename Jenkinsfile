pipeline {
    agent any

    stages {
        stage('Dockerize simple nodejs app') {
            environment {
                SERVICE_CREDS = credentials('docker_cred')
            }
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/anas1243/Deploy-python-redis-app-on-GKE-using-jenkins']]])
                    
                sh "docker build -t anas1243/python-redis-app:$BUILD_NUMBER  -f App/Dockerfile ." 
                sh "docker login -u $SERVICE_CREDS_USR -p $SERVICE_CREDS_PSW"
                sh "docker push anas1243/python-redis-app:$BUILD_NUMBER"
                    
            }
        }
    }
    post {
        success {
            echo "wallah w 3mloha el regala"
        }
    }
}