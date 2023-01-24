pipeline {
    agent any
    stages {
        stage('Install CLIs') {
            steps {
                sh "sudo chmod +x *.sh"
                sh "./install-cli.sh"
                sh "./install-eksctl.sh"
                sh "./install-kubectl.sh"
            }
        }
        stage('Configure kubectl') {
            steps {
                sh "aws eks --region eu-west-1 update-kubeconfig --name ClusterTest2"
            }
        }
        stage('Deploy manifests') {
            steps {
                sh "kubectl apply -f backend.yaml"
                sh "kubectl apply -f frontend.yaml"
                sh "kubectl get services"
            }
        }
    }
}