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
        nexusArtifactUploader artifacts: [[artifactId: 'vproArtifact', classifier: '', file: 'target/vprofile-v1.war', type: 'war']], credentialsId: '3bc13186-950a-479d-9916-62b85aff640d', groupId: 'pro', nexusUrl: '65.0.104.251:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'EGA', version: '$BUILD_ID'
      }
    } 
   }
 }
