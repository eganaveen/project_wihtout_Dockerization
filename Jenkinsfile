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
      steps{
        withSonarQubeEnv('sonarqube-6'){
          sh 'mvn sonar:sonar'
        }
      }
    }
   }
 }
