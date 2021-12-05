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
                GIT_TAG = "VersionNumber (versionNumberString: '${BUILD_DATE_FORMATTED, "yyyyMMdd"}-develop-${BUILDS_TODAY}')"
		}
	    steps {
		    checkout([$class: 'GitSCM', branches: [[name: '*/develop']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-cred', url: 'git@github.com:akashkadao/multibranch-pipeline-demo.git']]])
		    	sh "git tag"
			sh "git tag \$GIT_TAG"
			sh "git push origin \$GIT_TAG"
			
		}
	    }     
    }
}
