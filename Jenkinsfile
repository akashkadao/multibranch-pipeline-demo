pipeline { 
    agent any
    stages {
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
            environment { 
                GIT_TAG = "Release_version-$BUILD_NUMBER" 
                BUILD_VERSION = "version-$BUILD_VERSION"
            }
            steps {
                sh '''
                    git tag -a \$GIT_TAG \$BUILD_VERSION-m 'New Tag, New Build & New Build-Number'
                    git tag
                    git push origin develop \$GIT_TAG 
                   '''             
            }
        }     
    }
}
