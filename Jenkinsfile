pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'micro-eks', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://14750CA5E1417E3E71C6649B3A89D8F8.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl delete -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'micro-eks', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://14750CA5E1417E3E71C6649B3A89D8F8.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
