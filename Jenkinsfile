pipeline {
    agent {
      label 'docker'
    }

    stages {
        stage('Checkout git') {
            steps {
                dir('kibana-role') {
                    git branch: 'test', credentialsId: '5560fca1-a24d-48f9-b9c2-0204f2cab035', url: 'git@github.com:rdegtyarev/kibana-role.git'
                }
            }
        }
        stage('Install requirements') {
            steps {
                dir('kibana-role') {
                    sh 'pip install -r test-requirements.txt'
                }
            }
        }
        stage('Run molecule') {
            steps {
                dir('kibana-role') {
                    sh 'molecule test'
                }
            }
        }
        stage('Clean ws') {
            steps {
                cleanWs()
            }
        }
    }
}
