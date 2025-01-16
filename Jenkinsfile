pipeline{
    agent {label 'aniket'}
    stages{
        stage("clone the code"){
            steps{
                sh "whoami"
                git url: "https://github.com/AniketGirigoud/django-notes-app.git", branch:"main"
            }
        }
        stage("build stage"){
            steps{
                sh "docker build -t django-app:latest ."
            }
        }
        stage("docker push"){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerhubcred", usernameVariable:"dockerhubuser", passwordVariable:"dockerhubpass")]){
                sh "docker login -u ${env.dockerhubuser} -p ${env.dockerhubpass}"
                sh "docker image tag django-app ${env.dockerhubuser}/django-app:latest"
                sh "docker push ${env.dockerhubuser}/django-app:latest"
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
