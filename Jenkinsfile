@Library('SharedLibrary') _
pipeline {
    agent { label 'Gurav' }
    stages {
        stage('Hello') {
            steps {
                script {
                    hello()
                }
            }
        }
        stage('Clone') {
            steps {
                script {
                clone("https://github.com/shubhamgurav380/node-todo-cicd.git", "master")
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    docker_build("todo-app", "latest", "shubhamgurav380")
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the code'
            }
        }
        stage('Push') {
            steps {
                script {
                    docker_push("todo-app", "latest","shubhamgurav380")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the code'
                /* sh "docker run -d -p 8000:8000 todo-app:latest" */
                sh "docker compose down && docker compose up -d --build"
            }
        }
    }
}
