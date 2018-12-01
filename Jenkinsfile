pipeline {
    agent any

    parameters {
        string(defaultValue: "TEST", description: 'What environment?', name: 'userFlag')
        choice(choices: ['US-EAST-1', 'US-WEST-2'], description: 'What AWS region?', name: 'region')
    }
    
    options {
    buildDiscarder(logRotator(numToKeepStr:'3'))
    timestamps()
    timeout(time: 120, unit: 'MINUTES')
    }
    
   withCredentials([usernamePassword(credentialsId: 'af6bc4ec-4f53-4926-87a8-490c8446cfd5', passwordVariable: 'password1', usernameVariable: 'user1')]) {
       // some block
   }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh "echo ${params.userFlag}"
                sh "echo ${params.region}"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
