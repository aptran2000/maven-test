pipeline {
  agent any
  stages {
    stage('Unit Test') { 
      steps {
        sh 'mvn clean test'
      }
    }
	stage('Build') { 
		steps {
			withMaven(maven:'maven'){
				sh 'mvn -f maven-test/pom.xml clean install'
			}
		}
    }
    stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
      steps {
		withMaven(maven:'maven'){
			sh 'mvn -f maven-test/pom.xml package deploy -Danypoint.username=${ANYPOINT_CREDENTIALS_UN} -Danypoint.password=${ANYPOINT_CREDENTIALS_PWD} -DmuleDeploy'
		}
      }
    }
  }
}