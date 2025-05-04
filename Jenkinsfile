pipeline {
    agent any
    
    environment {
        SONARQUBE_SERVER = 'SonarQube' 
        DOCKER_IMAGE = 'image_ds2:latest'
    }
    
    stages {
        stage('Clone from GitHub') {
            steps {
                git branch: 'main', 
                url: 'https://github.com/Moetaz101/DS2.git'
            }
        }
        
        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar' 
                }
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE} .'
            }
        }
        
        stage('Push Docker Image') {  
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', '484ecd4e-f719-4450-8a76-5c39b292a2ff') {
                        docker.image("${DOCKER_IMAGE}").push()
                    }
                }
            }
        }
    }
    
    post {
        always {
            cleanWs() // Clean workspace
        }
    }
}