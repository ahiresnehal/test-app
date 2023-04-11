pipeline {
    agent any
    environment {
       email_list = 'snehalahire107@gmail.com'
   }
    stages {
        stage('Build') {
            steps {
                
                git 'https://github.com/ahiresnehal/test-app.git'

                 }
            }
        stage('Code Quality Check via SonarQubes'){
            steps {
               script {
               def scannerHome = tool 'SonarScanner';
                   withSonarQubeEnv("SonarScanner") {
              
                   sh "${tool("SonarScanner")}/bin/sonar-scanner"
                       }
                   }
                }
        }
        stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
        }
}
}
