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
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker build -t dipenshr/test_laravel_api_base_image:${BUILD_NUMBER} .'
            }
        }
        stage('Push') {
            steps {
                withCredentials([string(credentialsId: 'dockerpwd', variable: 'dockerpwd')]) {
                    sh 'docker login -u myotheremil@gmail.com -p ${dockerpwd}'
                    sh 'docker push dipenshr/test_laravel_api_base_image:${BUILD_NUMBER}'
                }
            }
        }
    }
}