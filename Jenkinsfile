pipeline {
    agent any

    stages {
        stage('Omar') {
            steps {
             git branch: 'main', credentialsId: '27457916-0152-403d-aa24-71ad8d3b894b', url: 'https://github.com/yasseralhwetat/orange.git'
            }
        }
        stage('Khalil') {
            steps {
             sh 'docker build -t image-from-jenkins:v1 . '
            }
        }
        stage('Suleiman') {
            steps {
            sh  'echo done image creation'
            }
        }
    }
}
