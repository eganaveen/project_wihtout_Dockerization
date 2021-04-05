pipeline{
  agent any
   stages{
    stage('scm'){
      steps{
        //clone source code from SCM
        git 'https://github.com/eganaveen/projectwihtoutDockerization.git'
      }
    }
     stage('install'){
      steps{
        //test the source code.
        sh 'mvn install'
      }
    } 
    stage('upload to nexus repository'){
      steps{
        //upload artifact to nexus repository
        nexusArtifactUploader artifacts: [[artifactId: 'artifact_id', classifier: '', file: 'target/vprofile-v1.war', type: 'war']], credentialsId: '8c09a263-d6a3-40bc-862e-9e0eb1ed0bf1', groupId: 'group_id', nexusUrl: '65.0.104.251:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'EGA', version: '$BUILD_ID'
      }
    } 
   }
 }
