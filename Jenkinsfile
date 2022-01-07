pipeline {
    agent {
      label 'docker'
    }

    stages {
        stage('Checkout git') {
            steps {
                git branch: 'main', credentialsId: '5560fca1-a24d-48f9-b9c2-0204f2cab035', url: 'git@github.com:rdegtyarev/kibana-role.git'
            }
        }
        stage('Run molecule') {
            steps {
                sh 'cd kibana-role'
                sh 'pip install -r test-requirements.txt'
                sh 'molecule test'
            }
        }
        stage('stage 3') {
            steps {
                sh 'echo Stage 3'
            }
        }
    }
}
