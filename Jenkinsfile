pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/tKite/python-flask-docker.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.build("python-flask-docker")
                }
            }
        }

        stage('Save Artifact') {
            steps {
                script {
                    sh 'docker run --rm python-flask-docker tar -czvf app.tar.gz app.py'
                    archiveArtifacts artifacts: 'app.tar.gz'
                }
            }
        }
    }
}
