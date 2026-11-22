pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code retrieved from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-flask-app:latest .'
            }
        }

        stage('Test Application') {
            steps {
                sh 'docker run --rm cicd-flask-app:latest python -c "import app; print(app.home())"'
            }
        }
    }
}
