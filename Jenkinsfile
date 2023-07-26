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
                // Build the Docker image using the Dockerfile in the repository
                script {
                    def customImageTag = "orange-httpd:v1"
                    docker.build(customImageTag, '.')
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push the Docker image to Docker Hub registry
                script {
                    def customImageTag = "orange-httpd:v1"
                    docker.withRegistry('https://index.docker.io/v1/', 'ed22d543-8498-4f04-9fad-3b211f57f8a0') {
                        docker.image(customImageTag).push()
                    }
                }
            }
        }
    }
}

