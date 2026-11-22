pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'khaledhjila/cicd-flask-app'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Code retrieved from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:latest .'
            }
        }

        stage('Test Application') {
            steps {
                sh 'docker run --rm $DOCKER_IMAGE:latest python -c "import app; print(app.home())"'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                            )]) {
                    sh '''
                        set +x
                        echo "$DOCKERHUB_TOKEN" | docker login -u "$DOCKERHUB_USER" --password-stdin
                        docker push "$DOCKER_IMAGE:latest"
                        docker logout


