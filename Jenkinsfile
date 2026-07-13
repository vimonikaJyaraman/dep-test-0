pipeline {
    agent any
    

    stages {

        stage('Deploy') {
            steps {
                withKubeConfig([credentialsId: 'minikube-config']) {
                    script {
                        // Directly replace the placeholder in deployment.yaml
                        
                        // Apply the updated manifest
                        sh "kubectl apply -f k8s/deployment.yaml"
                        
                        // Rollout restart to ensure the new image is pulled
                        sh "kubectl rollout restart deployment/my-app"
                        sh "kubectl rollout status deployment/my-app"
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up the temporary file
            sh "rm -f k8s/deployment.yaml"
        }
    }
}
