@Library('aniket') _
pipeline{
    agent {label 'aniket'}
    stages{
        stage("clone the code"){
            steps{
                clone("https://github.com/AniketGirigoud/django-notes-app.git", "origin")
            }
        }
        stage("build stage"){
            steps{
                 dockerbuild("django-apps", "latest")
            }
        }
        stage("docker push"){
            steps{
                   push("dockerhubcred", "aniketgirigoud", "django-apps", "latest")
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
