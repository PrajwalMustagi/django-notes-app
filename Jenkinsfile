@Library('Shared')_
pipeline{
    agent { label 'dev-server'}
    
    stages{
        stage("Code clone"){
            steps{
                sh "whoami"
            clone("https://githu@Library("shared") _

pipeline {

    agent { label 'vinod' }

    stages {

        stage('code clone') {
            steps {
                script {
                    clone(
                        'https://github.com/PrajwalMustagi/django-notes-app.git',
                        'main'
                    )
                }
            }
        }

        stage('hello') {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('build') {
            steps {
                echo 'build started'
                script {
                    build('notes-app', 'latest', 'mustagi')
                }
            }
        }

        stage('pushing to docker hub') {
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

        stage('deployment') {
            steps {
                echo 'The deployment starts here'
                sh 'docker compose up -d'
            }
        }
    }
}b.com/LondheShubham153/django-notes-app.git","main")
            }
        }
        stage("Code Build"){
            steps{
            dockerbuild("notes-app","latest")
            }
        }
        stage("Push to DockerHub"){
            steps{
                dockerpush("dockerHubCreds","notes-app","latest")
            }
        }
        stage("Deploy"){
            steps{
                deploy()
            }
        }
        
    }
}
