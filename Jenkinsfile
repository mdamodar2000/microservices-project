pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-damu', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://BD4695B90FE2EBD285226E3014405ACD.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-damu', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://BD4695B90FE2EBD285226E3014405ACD.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
