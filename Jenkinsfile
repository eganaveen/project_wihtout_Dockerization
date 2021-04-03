pipeline{
  agent any
  tools{
    maven "Maven"
  }
  stages{
    stage('scm'){
      steps{
        //clone source code from SCM
        git 'https://github.com/eganaveen/VProfile.git'
      }
    }    
  }
}
