pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-mka', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://8962FC61514FFFF81087F6FBAD68A128.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-mka', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://8962FC61514FFFF81087F6FBAD68A128.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
