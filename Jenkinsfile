pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig([credentialsId: 'k8-token', serverUrl: 'https://99D7A543DF90437DFE68D9A480D6B881.gr7.us-east-1.eks.amazonaws.com', clusterName: 'SHOYEBEKS-1', namespace: 'webapps']) {
                    sh 'kubectl apply -f deployment-service.yml'
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeConfig([credentialsId: 'k8-token', serverUrl: 'https://99D7A543DF90437DFE68D9A480D6B881.gr7.us-east-1.eks.amazonaws.com', clusterName: 'SHOYEBEKS-1', namespace: 'webapps']) {
                    sh 'kubectl get svc -n webapps'
                }
            }
        }
    }
}
