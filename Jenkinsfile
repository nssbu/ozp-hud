pipeline {
    agent {
        label 'KZ01_TI-141_OZP_CentOS'
    }
    stages {
        stage('Clear the workspace') {
            steps {
                sh 'sudo rm -rf *'
            }
        }
        stage('Checkout Repo') {
            steps {
                git url: 'http://www.github.com/mark-betters-ozp-forks/ozp-hud.git', branch: 'master'
            }
        }
        stage('Build') {
            steps {
                sh '''
                  npm install bower gulp
                  npm install; npm run build; npm run tarDistDate
                  mv *.tar.gz hud.tar.gz
                '''
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'hud.tar.gz'
            }
        }
    }
}