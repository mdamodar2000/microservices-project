pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-kinnu', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://41C92031B3DCE7AF8914E463F1A1BAE0.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-kinnu', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://41C92031B3DCE7AF8914E463F1A1BAE0.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
