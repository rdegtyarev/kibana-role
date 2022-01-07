pipeline {
    agent {
      label 'docker'
    }

    stages {
        stage('prepare') {
            steps {
                git branch: 'main', credentialsId: '5560fca1-a24d-48f9-b9c2-0204f2cab035', url: 'git@github.com:rdegtyarev/kibana-role.git'
                sh 'cd kibana-role'
                sh 'pip install -r test-requirements.txt'
                sh 'molecule test'
            }
        }
    }
}
