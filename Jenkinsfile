pipeline {
    agent any
    stages {
        stage('git clone') {
            steps {
                git credentialsId: 'git_url', url: 'https://github.com/akashkadao/multibranch-pipeline-demo.git'
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
                    git tag -a vo.1 -m 'this is for release version'
                    git tag -l
                    git push origin vo.1
                    '''
            }
        }        
    }
}
