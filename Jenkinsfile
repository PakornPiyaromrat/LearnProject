// CODE_CHANGES = getGitChanges()
def groovy
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

        stage('init') {
			steps {
                script {
                    groovy = load "script.groovy"
                }
			}
		}
		
		stage('build') {
			steps {
				script {
                    groovy.buildApp()
                }
			}
		}
		
		stage('test') {
            when {
                expression {
                    params.executeTests     //params.executeTets = params.executeTests == true
                }
            }
			steps {
				script {
                    groovy.testApp()
                }
			}
		}
		
		stage('deploy') {
			steps {
				script {
                    groovy.deployApp()
                }
		}
	}
}

node {
	//groovy script
	
}
