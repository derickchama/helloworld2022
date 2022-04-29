pipeline {
    agent any 
    tools {
    maven 'M2_HOME'
    }
    environment {
    registry = "derickch/devops_pipeline"
    registryCredential = 'dockerID'
    }
    stages {
        stage('Build') { 
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
        stage('Deploy') { 
            steps {
             script {
                docker.build registry + ":$BUILD_NUMBER"
              }
            }
        }
    }
}
