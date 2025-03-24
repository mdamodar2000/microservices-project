pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham007', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://95E639F6DAA34A73734F9051906EDF25.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham007', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://95E639F6DAA34A73734F9051906EDF25.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
