pipeline {
    agent any

    environment {
        // Define DockerHub credentials ID
        DOCKER_HUB_CREDENTIALS_ID = 'docker-hub-credentials2'
        // Define repository on Docker Hub
        DOCKER_REPO_PREFIX = 'muhammadranaumerofficial754/schoolmanagementsystem'
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the code from GitHub
                git 'https://github.com/yourusername/yourrepository.git'
            }
        }

        stage('Build and Push Docker Images') {
            steps {
                script {
                    // Build and push each service
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_HUB_CREDENTIALS_ID) {
                        // List all services to build and push
                        def services = [
                            'auth_backend_21i1184',
                            'classrooms_backend_21i1184',
                            'client_frontend_21i1184',
                            'event-bus_backend_21i1184',
                            'post_backend_21i1184'
                        ]

                        // Iterate over each service defined in the Docker Compose
                        services.each {
                            def app = docker.build("${DOCKER_REPO_PREFIX}/${it}", "./${it}")
                            app.push('latest')
                        }
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Use Docker Compose to deploy
                    sh 'docker-compose up -d'
                }
            }
        }

        stage('Validate Deployment') {
            steps {
                script {
                    // Implement your validation checks here
                    echo 'Running validation tests...'
                    // Example: curl to check if services are up and running
                    sh 'curl -f http://localhost:8412'
                    sh 'curl -f http://localhost:8413'
                    sh 'curl -f http://localhost:8411'
                    sh 'curl -f http://localhost:8414'
                    sh 'curl -f http://localhost:8415'
                }
            }
        }
    }

    post {
        always {
            // Cleanup after pipeline execution
            sh 'docker-compose down'
        }
    }
}
