pipeline {
   agent any
   options {
        ansiColor('xterm')
        timeout(5)
        timestamps()
    }
   stages {
      stage('Git Checkout') {
         steps {
             git branch: 'mavenWrapper', credentialsId: '4bf5a05b-27cb-4797-9d2f-22aa794f9650', url: 'https://github.com/pawel28/junit4.git'
         }
      }
      stage("Run project") {
          steps {
              sh './mvnw clean verify'
          }
      }
      stage("Collect results") {
          steps {
              junit 'target/surefire-reports/*.xml'
          }
      }
   }
}
