@Library("shared") _
pipeline {
    agent { label "vinod" }

    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script{
                code_checkout("https://github.com/iam-pratap/django-notes-app.git", "main")
                }
            }
        }
        stage("Build") {
            steps {
                script{
                docker_build("notes-app","latest","pratap15")
                }
                
            }
        }
        stage("push to docker") {
            steps {
                script{
                docker_push("notes-app","latest","pratap15")
                
                }
            }
        }
        
        
        stage("Deploy") {
            steps {
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
