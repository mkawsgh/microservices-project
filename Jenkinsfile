pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-mka', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://3C06F6B22D341B6C6422131481BE52C3.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-mka', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://3C06F6B22D341B6C6422131481BE52C3.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
