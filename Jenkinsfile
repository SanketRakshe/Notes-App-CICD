@Library("shared") _
pipeline{
    
    agent { label "sanket"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Code"){
            steps{
               script{
                clone("https://github.com/SanketRakshe/Notes-App-CICD.git","master")
               }
            }
        }
        
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","sanketrakshe")
                }
            }
        }
        
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","sanketrakshe")
                }
            }
        }
        
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
