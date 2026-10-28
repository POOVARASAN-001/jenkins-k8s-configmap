
pipeline {
    agent any

    environment {
        KUBECTL = 'D:\\DockerApp\\resources\\bin\\kubectl.exe'
        KUBECONFIG = 'C:\\Users\\POOVARASAN\\.kube\\config'
    }

    stages {
        stage('Create ConfigMap') {
            steps {
                bat '"%KUBECTL%" apply -f configmap.yaml'
            }
        }

        stage('Deploy Application') {
            steps {
                bat '"%KUBECTL%" apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat '"%KUBECTL%" rollout status deployment/configmap-app --timeout=180s'
                bat '"%KUBECTL%" get configmap web-config'
                bat '"%KUBECTL%" get pods -l app=configmap-app'
            }
        }
    }
}
