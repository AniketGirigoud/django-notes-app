@Library("sharedaniket") _
pipeline{
    agent {label "boss"}
    
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    gitclone("https://github.com/AniketGirigoud/django-notes-app.git","main")
                }
            
            }
            
        }
        stage("Build"){
            steps{
                script{
                    build("django-app","latest","aniketgirigoud")
                }
                
             
            }
        }
        stage("pushing image to dockerhub"){
            steps{
                script{
                    push("django-app", "latest", "aniketgirigoud" )
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploy the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}

