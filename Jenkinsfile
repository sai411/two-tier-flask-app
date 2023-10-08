pipeline {
    agent any

    environment {
        docker_image = "sai411/flask_img_2_tire:${env.BUILD_NUMBER}"
        docker_image_latest = "sai411/flask_img_2_tire:latest"
    }

    stages {
        stage("git scm") {
            steps{
            echo "git clone"
        }
        }
        stage("docker build and push") {
            steps {
                script {
                    sh "docker build -t ${docker_image} ."
                    sh "docker tag ${docker_image} ${docker_image_latest}"
                    // add the credentails in jenkins 
                    // empty url here uses docker hub
                    docker.withRegistry('', 'docker-cred'){
                        sh "docker push ${docker_image_latest}"
                        sh "docker push ${docker_image}"
                    }
                }
            }
        }

        stage("deployment") {
            steps {
                script {
                       
                    
                }
            }
        }
    }
}
