pipeline {
    agent any
    stages {
        stage('git clone') {
            steps {
                git credentialsId: 'git', url: 'https://github.com/akashkadao/multibranch-pipeline-demo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'echo package'
            }
        }
        stage('Test') {
            steps {
                sh 'echo check'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying only because this commit is tagged...'
                sh 'echo deploy'
            }
        }
        stage('git tags') {
            steps {
                sh '''
                    git tag -a ${BUILD_NUMBER} -m 'this is for release version'
                    git tag -l
                    git push origin ${BUILD_NUMBER}
                    '''
            }
        }        
    }
}
