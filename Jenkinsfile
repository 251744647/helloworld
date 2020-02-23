pipeline {
    agent {
        node { label 'DEVOPS' }
    }
    parameters {
        string(name: 'new_version', description: 'deployed version')
    }
    stages {
        stage('Deploy Helloworld') {
            steps {
                sh (script:"""
                    new_version=${new_version:-latest}
                    kubectl apply -f deploy.yaml
                """)
            }
        }
    }
    post {
        always {
            echo 'Clean up the job workspace'
        }
    }
}
