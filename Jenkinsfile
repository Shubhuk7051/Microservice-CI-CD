pipeline {
    agent any

    stages {
        stage('Deploy to K8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-11microsvcs', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://A62534EEE33EFFAD3850037C3B497546.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
    }
    
    stages {
        stage('Verify Deployments') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-11microsvcs', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://A62534EEE33EFFAD3850037C3B497546.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
