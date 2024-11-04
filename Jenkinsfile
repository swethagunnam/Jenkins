pipeline {
    agent any
    // environment {
    //     IMAGE_NAME = 'sanjeevkt720/jenkins-flask-app'
    //     IMAGE_TAG = "${IMAGE_NAME}:${env.BUILD_NUMBER}"
    //     KUBECONFIG = credentials('kubeconfig-credentials-id')

    // }
    environment {
        SERVER_CREDS = credentials("server-creds")
    }
    stages {
        //---It occurs by default
        // stage('Checkout') {
        //     steps {
        //         git url: 'https://github.com/swethagunnam/Jenkins.git', branch: 'main'
        //         sh "ls -ltr"
        //     }
        // }
        stage('Setup') {
            steps {
                echo "Username & password is: ${SERVER_CREDS}"
                sh "pip3 install -r requirements.txt"
            }
        }
        stage('Test') {
            steps {
                echo "Username is: ${SERVER_CREDS_USR}"
                 echo "Password is: ${SERVER_CREDS_PSW}"
                sh "pytest"
                sh "whoami"
            }
        }

        // stage('Login to docker hub') {
        //     steps {
        //         withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
        //         sh 'echo ${dockerhubpwd} | docker login -u sanjeevkt720 --password-stdin'}
        //         echo 'Login successfully'
        //     }
        // }
        // stage('Build Docker Image')
        // {
        //     steps
        //     {
        //         sh 'docker build -t ${IMAGE_TAG} .'
        //         echo "Docker image build successfully"
        //         sh "docker images"
        //     }
        // }
        // stage('Push Docker Image')
        // {
        //     steps
        //     {
        //         sh 'docker push ${IMAGE_TAG}'
        //         echo "Docker image push successfully"
        //     }
        // }
        // stage('Deploy to EKS Cluster') {
        //     steps {
        //         sh "kubectl apply -f deployment.yaml"
        //         echo "Deployed to EKS Cluster"
        //     }
        // }
    }
}