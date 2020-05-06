pipeline {
    agent any
    tools {nodejs 'node'}
    stages {
        stage('NPM Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Docker Build') {
            steps {
                script {
                  checkout scm
                    def customImage = docker.build("my-app")

                    customImage.inside {
                        sh 'make test'
                    } 
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}