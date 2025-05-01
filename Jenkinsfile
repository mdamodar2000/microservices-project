pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-damodar12', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://01754DA9D01E9CFDBE810240EA4DC2FF.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-damodar12', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://01754DA9D01E9CFDBE810240EA4DC2FF.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
