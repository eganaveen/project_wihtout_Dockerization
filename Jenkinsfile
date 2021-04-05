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
    stage('upload to nexus repository'){
      steps{
        //upload artifact to nexus repository
        nexusArtifactUploader artifacts: [[artifactId: 'vprofile', classifier: '', file: 'target/vprofile-v1.war', type: 'war']], credentialsId: '745aed4d-b53b-42f1-876d-e40529b73c1d', groupId: 'pro', nexusUrl: '13.126.34.226:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'EGA', version: '$BUILD_ID'
      }
    } 
   }
 }
