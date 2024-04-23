pipeline {
    agent any
    stages {
        // stage('Checkout') {
        //     steps {
        //         git 'https://github.com/hoanglinhdigital/nodejs-random-color.git'
        //     }
        // }

        stage('Build') {
            steps {
                sh 'docker build -t nodejs-random-color:v__${BUILD_ID} .'
            }
        }
        stage('Upload image to ECR') {
            steps {
                sh 'aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 471112707283.dkr.ecr.ap-southeast-1.amazonaws.com'
                sh 'docker tag nodejs-random-color-hiumx:v__${BUILD_ID} 471112707283.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color-hiumx:v__${BUILD_ID}'
                sh 'docker push 471112707283.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color-hiumx:v__${BUILD_ID}'
            }
        }
    }
}
