pipeline {
    agent any

    stages {
        stage('K8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-cred', namespace: 'webapps', serverUrl: 'https://65CD09EFA0CC26D453E759CC5253F6E7.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                sleep 60
                }
            }
        }
        stage('Verify Deploy') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-cred', namespace: 'webapps', serverUrl: 'https://65CD09EFA0CC26D453E759CC5253F6E7.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
