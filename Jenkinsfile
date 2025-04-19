pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-Jenkins', contextName: '', credentialsId: 'k8s-token', namespace: 'eksjenkins', restrictKubeConfigAccess: false, serverUrl: 'https://D2AAAE941380E7C45B5C118C72339987.gr7.us-east-1.eks.amazonaws.com'){
                 sh 'kubectl apply -f deployment-service.yml'
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-Jenkins', contextName: '', credentialsId: 'k8s-token', namespace: 'eksjenkins', restrictKubeConfigAccess: false, serverUrl: 'https://D2AAAE941380E7C45B5C118C72339987.gr7.us-east-1.eks.amazonaws.com'){ 
                 sh 'kubectl get svc -n eksjenkins'
                }
            }
        }
    }
}
