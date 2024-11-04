pipeline {
    agent any
    // environment {
    //     IMAGE_NAME = 'sanjeevkt720/jenkins-flask-app'
    //     IMAGE_TAG = "${IMAGE_NAME}:${env.BUILD_NUMBER}"
    //     KUBECONFIG = credentials('kubeconfig-credentials-id')

    // }
    stages {
        //---It occurs by default
        // stage('Checkout') {
        //     steps {
        //         git url: 'https://github.com/swethagunnam/Jenkins.git', branch: 'main'
        //         sh "ls -ltr"
        //     }
        // }
        stage('Setup') {
            environment {
                DB_HOST = '168.89.09'
                USERNAME = "Swetha"
                PASSWORD = "Swetha@123"
            }
            steps {
                sh "pip3 install -r requirements.txt"
                echo "The database host is ${DB_HOST}"
            }
        }
        stage('Test') {
            steps {
                sh "pytest"
                sh "whoami"
                echo "Commit is ${env.GIT_COMMIT}"
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