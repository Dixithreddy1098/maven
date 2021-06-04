pipeline {
    agent any
  stages {
    stage('Downloading the code') {
      steps{
        git credentialsId: 'Git', 
        url: 'https://github.com/Dixithreddy1098/maven'
        echo 'Downloaded the Code from the SCM'
      }
    stage('Testing and validating')
      steps{
        mvn '-B -DskipTests clean package'
        mvn 'test'
        echo 'Tesing and validating the code '
      }
      stage('Artifract'){
        steps{
          archiveArtifacts artifacts: '**/*.war'
          echo "Creating the Atrifact"
        }
      }
  }
    post{
      always {
        cleanWs()
      }
      success{
        message 'The job is successful'
      }
      failure{
        message 'The job is failed'
      }       
    }
}
  
