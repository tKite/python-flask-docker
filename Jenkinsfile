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

        stage('Save Artifacts') {
            steps {
                script {
                    sh 'docker create --name temp_container python-flask-docker'
                    sh 'mkdir -p /var/lib/jenkins/workspace/project/artifacts'
                    sh 'docker cp temp_container:/app/. /var/lib/jenkins/workspace/project/artifacts'
                    sh 'docker rm temp_container'
                    archiveArtifacts artifacts: '/var/lib/jenkins/workspace/project/artifacts/*'
                }
            }
        }
    }
}

