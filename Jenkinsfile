pipeline {
    agent any
    stages {
        stage('Clone repository'){
            steps{
                checkout([$class:'GitSCM',
                          branches:[[name: '*/main]],
                          userRemoteConfigs: [[url: 'https://github.com/Wootzgold/PES1UG21CS150_Jenkins/Jenkins.git]]])
            }
        }
        stage('Build') {
            steps {
              build 'PES1UG21CS150-1'
              sh 'g++ main.cpp -o output'
            }
        }

        stage('Test') {
            steps {
                sh './output'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying...'
                }
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed.'
        }
    }
}
