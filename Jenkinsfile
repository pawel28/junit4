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
}pipeline {
    environment {
        MESSAGE = "dupa mesydz"
        MY_CRED = credentials("leman")
    }
   agent any
   parameters {
            credentials credentialType: 'com.cloudbees.plugins.credentials.impl.UsernamePasswordCredentialsImpl', defaultValue: '', description: '', name: 'credentials_env', required: true
            string defaultValue: 'TEST', description: 'Some Description', name: 'deplpyEnv', trim: false
            booleanParam defaultValue: false, description: '', name: 'forceDeployForTheSameVersion'
    }
   stages {
      stage('Hello stage') {
         steps {
            echo 'Hello from Declarative pipeline!'  
            sh 'java -version'
         }
      }
      stage("BLabla stejdza") {
          steps {
              echo "${MESSAGE}"
              echo "${params.deplpyEnv}"
              echo "${params.forceDeployForTheSameVersion}"
              
              echo "$MY_CRED_USR"
              echo "$MY_CRED_PSW"
          }
      }
      stage("Deploy") {
          input {
                message 'Are You Sure?'
                parameters {
                    booleanParam defaultValue: false, description: '', name: 'Sure'
                }
            }
          steps {
              echo "Stejdz Deploy"
              echo "$Sure"
          }
     
      }
   }
}
