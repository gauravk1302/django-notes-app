@Library("Shared") _
pipeline {
    agent { label 'agent' }

    stages {
        stage('Hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
               script{
                clone("https://github.com/gauravk1302/django-notes-app.git","main")
                echo 'code cloned successfully'
                   
               }
            }
        }

        stage('Build') {
            steps {
                script{
                    docker_build("notes-app","latest","gauravk1302")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script{
                    docker_push("notes-app","latest","gauravk1302")
                 
                }
            }
        }

        stage('Deploy') {
            steps {
                sh "docker compose down"
                sh "docker compose up -d"
            }
        }
    }
}
