pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'apt update && curl -fsSL https://get.docker.com | sh'
                sh 'usermod -aG docker jenkins'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker build -t test_laravel_api_base_image:${BUILD_NUMBER} .'
	            sh 'docker tag test_laravel_api_base_image dipenshr/test_laravel_api_base_image:${BUILD_NUMBER}'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'myotheremil@gmail.com', passwordVariable: 'j%]u(n]vM2D_F=R')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'docker push dipenshr/test_laravel_api_base_image:${BUILD_NUMBER}'
                }
            }
        }
    }
}