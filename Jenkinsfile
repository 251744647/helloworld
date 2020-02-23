pipeline {
    agent {
        node { label 'DEVOPS' }
    }
    parameters {
        string(name: 'new_version', defaultValue: 'latest', description: 'deployed version')
    }
    stages {
        stage('Deploy Helloworld') {
            steps {
                sh (script:"""
                    echo "${new_version}"
                    sed -i "s/new_version/${new_version}/" deploy.yaml
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
