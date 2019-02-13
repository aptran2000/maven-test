pipeline {
  agent any
  environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
  stages {
    stage('Unit Test') { 
      steps {
      	withMaven(maven:'maven'){
        	sh 'mvn -f pom.xml clean test'
        }
      }
    }
	stage('Build') { 
		steps {
			withMaven(maven:'maven'){
				sh 'mvn -f pom.xml clean install'
			}
		}
    }
    stage('Deploy') { 
      steps {
		withMaven(maven:'maven'){
			sh 'mvn -f pom.xml package deploy -Danypoint.username=${ANYPOINT_CREDENTIALS_UN} -Danypoint.password=${ANYPOINT_CREDENTIALS_PWD} -DmuleDeploy'
		}
      }
    }
  }
}