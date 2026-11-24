pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MyEks01', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://4F4FA33A5895CDFEEF6F95B84D4C328F.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MyEks01', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://4F4FA33A5895CDFEEF6F95B84D4C328F.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
