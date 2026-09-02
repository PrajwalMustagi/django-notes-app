@Library('Shared') _

pipeline {

    agent { label 'vinod' }

    stages {

        stage('Code clone') {
            steps {
                script {
                    clone(
                        'https://github.com/PrajwalMustagi/django-notes-app.git',
                        'main'
                    )
                }
            }
        }

        stage('Hello') {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Build started'

                script {
                    build('notes-app', 'latest', 'mustagi')
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                echo 'The image is being pushed to Docker Hub'

                withCredentials([
                    usernamePassword(
                        credentialsId: 'mustagi',
                        passwordVariable: 'dockerhubpass',
                        usernameVariable: 'dockerhubuser'
                    )
                ]) {

                    sh 'echo $dockerhubpass | docker login -u $dockerhubuser --password-stdin'

                    pushcode('notes-app', 'latest', 'mustagi')
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment starts here'

                sh 'docker compose down && docker compose up -d'
            }
        }
    }
}
