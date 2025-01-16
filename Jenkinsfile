@Library("aniket")_
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
                    build( "django-apps", "latest")
                }
            }
        }
        stage("docker push"){
            steps{
               script{
                   push("dockerhubcred","aniketgirigoud", "django-apps","latest")
               }
                }
            }
        }
        stage("deoloy the code"){
            steps{
                script{
                    compose()
                }
            }
        }
        stage("wel done"){
            steps{
                script{
                    hello()
                }
            }
        }
    }

