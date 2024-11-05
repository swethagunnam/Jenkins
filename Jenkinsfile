pipeline {
    agent any
    // environment {
    //     IMAGE_NAME = 'sanjeevkt720/jenkins-flask-app'
    //     IMAGE_TAG = "${IMAGE_NAME}:${env.BUILD_NUMBER}"
    //     KUBECONFIG = credentials('kubeconfig-credentials-id')

    // }
    options {
        timeout(time: 1, unit: 'MINUTES')
    }
    stages {
        //---It occurs by default
        // stage('Checkout') {
        //     steps {
        //         git url: 'https://github.com/swethagunnam/Jenkins.git', branch: 'main'
        //         sh "ls -ltr"
        //     }
        // }
        stage('lint and format'){
            steps{
                sh "sleep 70"
            }
        }
        stage('Setup') {
            steps {
                withCredentials([usernamePassword(credentialsId:'server-creds',
                usernameVariable:"myuser", passwordVariable:"mypassowrd",)]){
                    sh '''
                    echo "My username is ${myuser}
                    echo "My password id ${mypassword}
                    '''
                }
                sh "pip3 install -r requirements.txt"
            }
        }
        stage('Test') {
            steps {
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