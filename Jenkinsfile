pipeline {
    agent {
      label 'docker'
    }

    stages {
        stage('Checkout git') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/test']], extensions: [], userRemoteConfigs: [[credentialsId: '5560fca1-a24d-48f9-b9c2-0204f2cab035', refspec: 'kibana-role', url: 'git@github.com:rdegtyarev/kibana-role.git']]])
            }
        }
        stage('Install requirements') {
            steps {
                sh 'pip install -r test-requirements.txt'
            }
        }
        stage('Run molecule') {
            steps {
                sh 'molecule test'
            }
        }
        stage('Clean ws') {
            steps {
                cleanWs()
            }
        }
    }
}
