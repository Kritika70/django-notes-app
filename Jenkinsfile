@Library("Shared") _
pipeline {
    agent {label "kritika"}
    
    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Hey!"){
            steps{
                script{
                    newfile()
                }
            }
        }
        stage('Code') {
            steps {
                script{
                    clone("https://github.com/Kritika70/django-notes-app","main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    docker_build("notes-app","latest","kritikajain34")
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                script{
                    docker_push("notes-app","latest")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is a deploy part'
                sh "docker compose down && docker compose up -d "
            }
        }
    }
}
