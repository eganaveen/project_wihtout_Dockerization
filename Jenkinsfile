pipeline{
  agent any
   stages{
    stage('scm'){
      steps{
        //clone source code from SCM
        git 'https://github.com/eganaveen/projectwihtoutDockerization.git'
      }
    }
     stage('test'){
      steps{
        //test the source code.
        sh 'mvn test'
      }
    } 
    stage('Sonarqube') {
    environment {
        scannerHome = tool 'sonarqube'
    }
    steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
      sh '''sonar.projectKey=project1
sonar.projectName=project1
sonar.projectVersion=1.0
sonar.login=admin
sonar.password=admin
sonar.sources=.
sonar.binaries=target/classes/com/visualpathit/account/controller/
sonar.junit.reportsPath=target/surefire-reports
sonar.jacoco.reportPath=target/jacoco.exec'''
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
    }
   }
 }
