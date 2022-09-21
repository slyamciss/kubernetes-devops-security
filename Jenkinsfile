pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true" //so that they can be downloaded later
              archive 'target/*.jar'
            }
      }

      stage('Unit Tests') {
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
}