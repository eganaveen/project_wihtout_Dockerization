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
    
    stage('build'){
      steps{
        //generate artifact
        sh 'mvn package'
      }
    }
    
    stage('upload to nexus'){
      steps{
        //upload artifact to nexus repository
        nexusArtifactUploader artifacts: [[artifactId: 'vprofile', classifier: '', file: 'target/vprofile-v1.war', type: 'war']], credentialsId: '745aed4d-b53b-42f1-876d-e40529b73c1d', groupId: 'TESTSCM', nexusUrl: '13.233.212.205:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'vprofileN', version: '$BUILD_ID'
      }
    }
    
  }
}
