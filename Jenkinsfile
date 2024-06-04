pipeline {
    agent {
        kubernetes {
            label 'jenkins-agent'
            defaultContainer 'kubectl'
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    jenkins: agent
spec:
  containers:
  - name: kubectl
    image: bitnami/kubectl:latest
    command:
    - cat
    tty: true
"""
        }
    }
    stages {
        stage('Test Connection') {
            steps {
                container('kubectl') {
                    script {
                        sh 'kubectl version'
                        sh 'kubectl get nodes'
                    }
                }
            }
        }
    }
}
