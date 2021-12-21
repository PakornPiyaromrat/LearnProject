// CODE_CHANGES = getGitChanges()
pipeline {
	
	agent any
        environment {
                NEW_VERSION = '1.3.0'
                SERVER_CREDENTIALS = credentials('server-credentials')
        }
	stages {
		
		stage('build') {
//                         when {
//                                 expression {
//                                         BRANCH_NAME == 'dev' && CODE_CHANGES == true
//                                 }
//                         }
			steps {
				echo 'building the application...'
				echo 'built the application...'
                                echo "building version ${NEW_VERSION}"
			}
		}
		
		stage('test') {
                        when {
                                expression {
                                        BRANCH_NAME == 'dev'
                                }
                        }
			steps {
				echo 'testing the application...'
			}
		}
		
		stage('deploy') {
			steps {
				echo 'deploying the application...'
                                withCredentials([
                                        usernamePassword (credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)
                                ]) {
                                        sh "some script ${USER} ${PWD}"
                                }
		}	
	}
	post {
                always {
                }
                success {
                }
                failure {
                }
	}
}

node {
	//groovy script
	
}
