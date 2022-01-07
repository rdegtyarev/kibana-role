pipeline {
    agent {
      label 'docker'
    }

    stages {
        stage('Checkout git') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/test']], extensions: [], userRemoteConfigs: [[name: 'kibana-role', url: 'git@github.com:rdegtyarev/kibana-role.git']]])
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
