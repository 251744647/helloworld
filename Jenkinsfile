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
                    if [ "${new_version}" == '' ];then
                        new_version="latest"
                    fi
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
