pipeline {
    agent any
    tools{
        maven 'M2_HOME'
    }
    environment {
    registry = '663098898416.dkr.ecr.us-east-1.amazonaws.com/devop_repository'
    registryCredential = 'jenkins-ecr'
    
  }
    stages {
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/alldevice2018/helloworld_jan_22.git'
            }
        }
        stage('Code Build') {
            steps {
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
       
        stage('Deploy image') {
            steps{
                script{ 
                    docker.build Registry + ":$BUILD_NUMBER" {
                        dockerImage.push()
                    }
                }
            }
        }  
    }
}
