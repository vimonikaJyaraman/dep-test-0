stage('Deploy') {
    steps {
        withKubeConfig([credentialsId: 'minikube-config']) {
            script {
                // 1. Update the image
                sh "sed 's|IMAGE_PLACEHOLDER|${IMAGE_WITH_TAG}|g' k8s/deployment.yaml > k8s/deployment_updated.yaml"
                
                // 2. Apply (Kubernetes handles the rolling update automatically)
                sh "kubectl apply -f k8s/deployment_updated.yaml"
                
                // 3. Just wait for completion
                sh "kubectl rollout status deployment/my-app"
            }
        }
    }
}
