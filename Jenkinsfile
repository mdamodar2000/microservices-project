pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-damodar12', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://A35DFE15E49EE202B75DAA1A45F52A61.yl4.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-damodar12', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://A35DFE15E49EE202B75DAA1A45F52A61.yl4.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
