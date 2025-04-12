pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://F3F2B7C2BF5F34287F71DD212F680BA1.gr7.us-east-1.eks.amazonaws.com'){
                 sh 'kubectl apply -f deployment-service.yml'
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://F3F2B7C2BF5F34287F71DD212F680BA1.gr7.us-east-1.eks.amazonaws.com'){ 
                 sh 'kubectl get svc -n webapps'
                }
            }
        }
    }
}
