@Library("Shared") _

pipeline{
    agent any
    
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
           steps{
              script{
                  clone("https://github.com/ananth911/django-notes-app.git","main")
              }
                
           } 
        }
        stage("build"){
            steps{
                script{
                docker_build("notes-app","v2","ananthjain911")
                }
            }
        }
        stage("push to dockerhub"){
            steps{
                script{
                    docker_push("notes-app","v2","ananthjain911")
                 
                }
            }
        }
        stage("deploy"){
            steps{
                echo " this is deploy  stage"
                sh "docker compose down && docker compose up -d"
            }
            
        }
    }
    
}
