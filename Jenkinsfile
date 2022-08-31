pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    
    stages {
       stage('Build'){
          steps {
             sh 'maven clean'
             sh 'maven install'
             sh 'maven package'
                
          }
       }

       stage('Test'){
          steps {
             sh 'mvn test'
          }
       }
      
      stage('Deploy'){
          steps {
             echo 'Deploy step'
            sleep 10
          }
       }
      
      stage('Docker'){
          steps {
             echo 'Image step'
          }
       }         
    }
 }
