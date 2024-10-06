@Library("Shared") _
pipeline {
    
    agent { label "vinod" }
    
    stages{
        
        stage ("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage ("code"){
            steps{
                script{
                  clone("https://github.com/mayurpwr7/django-notes-app.git/","main")  
                }
            }
        }
        stage ("build"){
            steps{
                script{
                   docker_build("notes-app","latest","mayurpwr7")
                }
            }
        }
        stage("dockerhub"){
            steps{
                script{
                    docker_push("notes-app","latest","mayurpwr7")
                }
            }
            
        }
        stage("deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
                
            }
            
        }
    }
}
