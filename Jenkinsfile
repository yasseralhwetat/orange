pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
             git branch: 'main', credentialsId: '27457916-0152-403d-aa24-71ad8d3b894b', url: 'https://github.com/yasseralhwetat/orange.git'
            }
        }


        stage('Build Docker Image') {
            steps {
                script {
                    def customImageTag = "yasseralhwetat/orange-httpd:omar"
                    docker.build(customImageTag, '.')
                }
            }
        }


        stage('Push Docker Image') {
            steps {
                script {
                    def customImageTag = "yasseralhwetat/orange-httpd:omar"
                     withDockerRegistry(credentialsId: 'ed22d543-8498-4f04-9fad-3b211f57f8a0') {

                        docker.image(customImageTag).push()
                    }
                }
            }
        }

        stage('Build to kubernetes') {
            steps {

            sh  'kubectl apply -f .  --kubeconfig kubeconfig'
                    }

                }
            }


  }
