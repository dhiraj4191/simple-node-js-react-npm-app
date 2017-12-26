pipeline {
    agent { docker 'node:6' }
    stages {
        stage('Build') {
            steps {
                sh 'npm run test'
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                sshagent (credentials: ['jenkins-generated-ssh-key']) {
                    sh 'git push --tags'
                }
            }
        }
    }
}