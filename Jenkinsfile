@Library("aniket")_
pipeline{
    agent {label 'aniket'}
    stages{
        stage("clone the code"){
            steps{
                sh "whoami"
                    clone("https://github.com/AniketGirigoud/jenkins-shared-library/tree/main/vars" , "main")
            }
        }
        stage("build stage"){
            steps{
                 build( "django-apps", "latest")
            }
        }
        stage("docker push"){
            steps{
                   push("dockerhubcred","aniketgirigoud", "django-apps","latest")
           }
        }
        stage("deoloy the code"){
            steps{
               compose()
            }
        }
        stage("wel done"){
            steps{
                    hello()
            }
        }
    }
}
