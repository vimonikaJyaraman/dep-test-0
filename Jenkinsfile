pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl rollout status deployment/my-app'
            }
        }
    }
}
