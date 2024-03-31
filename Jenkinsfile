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

        stage('Save Executable Artifact') {
            steps {
                script {
                    sh 'docker run --rm python-flask-docker sh -c "cp /app/app.py /data/app.py"'
                    archiveArtifacts artifacts: 'app.py'
                }
            }
        }
    }
}
