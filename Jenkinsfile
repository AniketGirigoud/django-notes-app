pipeline{
    agent {label 'aniket'}
    stages{
        stage("clone the code"){
            steps{
                sh "whoami"
                script{
                    clone("https://github.com/AniketGirigoud/jenkins-shared-library/tree/main/vars" , "main")
                }
            }
        }
        stage("build stage"){
            steps{
                script{
                    build( aniketgirigoud/django-apps:latest)
                }
            }
        }
        stage("docker push"){
            steps{
               script{
                   push(aniketgirigoud/django-apps:latest)
               }
                }
            }
        }
        stage("deoloy the code"){
            steps{
                sh "docker-compose down && docker-compose up -d --build"
            }
        }
        stage("wel done"){
            steps{
                echo  "running successfully"
            }
        }
    }
}
