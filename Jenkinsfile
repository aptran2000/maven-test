pipeline {
  agent any
  stages {
    stage('Unit Test') { 
      steps {
        sh 'mvn clean test'
      }
    }
    stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
      steps {
        sh 'mvn deploy -P cloudhub -Dmule.version=3.9.0 -Danypoint.username=${ANYPOINT_CREDENTIALS_UN} -Danypoint.password=${ANYPOINT_CREDENTIALS_PWD} -Dmaven.repo.local="C:\Users\Anh\.m2\repository" --settings "C:\Users\Anh\.m2\settings.xml"' 
      }
    }
  }
}