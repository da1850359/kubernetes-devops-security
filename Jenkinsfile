pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar'
            }
        }  
      stage('Uit Tests - JUnit and Jacoco report') {
      steps {
        sh "mvn test"
      }
      post {
         always {
           junit 'target/surefire-reports/*.xml'
           jacoco execPattern: 'target/jacoco.exec'
        }
      }
    }
}