// CODE_CHANGES = getGitChanges()
pipeline {
	
	agent any
    parameters {
        //Use for expression can use in any stages
        // string(name: 'VERSION', defaultValue: '', description: 'version to deoploy on prod')
        choice(name: 'VERSION', choices: ['1.1', '1.2', '1.3'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
//     tools {
//         //Jenkinsfile only support 3 tools right now gradle, maven, jdk
//         maven 'Maven'
//     }
//     environment {
//         //Look all the command in localhost:8080/env-vars.html
//         NEW_VERSION = '1.3.0'
//         SERVER_CREDENTIALS = credentials('server-credentials')
//     }
	stages {
		
		stage('build') {
                        when {
                                expression {
                                        BRANCH_NAME == 'dev' && CODE_CHANGES == true
                                }
                        }
			steps {
				echo 'building the application...'
				echo 'built the application...'
                echo "building version ${NEW_VERSION}"
                echo 'mvn install'
			}
		}
		
		stage('test') {
            when {
                expression {
                    BRANCH_NAME == 'dev'
                    params.executeTests     //params.executeTets = params.executeTests == true
                }
            }
			steps {
				echo 'testing the application...'
			}
		}
		
		stage('deploy') {
			steps {
				echo 'deploying the application...'
                echo "deploying version ${params.VERSION}"
//                 withCredentials([
//                     usernamePassword (credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)
//                 ]) 
// 		{
//                     sh "some script ${USER} ${PWD}"
//                 }
		}	
	}
// 	post {
//         always {
//         }
//         success {
//         }
//         failure {
//         }
// 	}
}

node {
	//groovy script
	
}
