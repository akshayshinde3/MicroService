pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://EF7F817EB94DF58DA003327E7AD9274E.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh"kubectl apply -f deployment-service.yml"
             
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://EF7F817EB94DF58DA003327E7AD9274E.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh"kubectl get svc -n webapps"
                }
            }
        }
    }
}
