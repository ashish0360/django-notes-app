@Library("shared") _
pipeline{
    agent {label "jarvis"}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }    
        }
    
        stage("code"){
            steps{
                script{
                    clone("https://github.com/ashish0360/django-notes-app.git","main")
                }
            }
        }
        
        stage("build"){
            steps{
                script{
                    docker_build("note-app","latest","ashish2024ak")
                }
            }
        }
        
        stage("Pushing image to docker"){
            steps{
                script{
                    docker_push(Project: "note-app",ImageTag: "latest",dockerhubuser: "ashish2024ak")
                }
            }
        }
        
        
        stage("test"){
            steps{
                echo "This is testing code"
            }
        }
        
        stage("deploy"){
            steps{
                script{
                    docker_compose()
                    echo "Pipeline is working"
                }
            }
        }
    }
}
