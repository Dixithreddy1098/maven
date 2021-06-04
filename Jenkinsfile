pipeline {
    agent any 
    stages{
        stage('Downloading the code') {
            steps{
                git credentialsId: 'Git', 
                url: 'https://github.com/Dixithreddy1098/maven'
                echo 'Downloaded the Code from the SCM'
            }
        }
        stage('Testing and validating'){
            steps{
                sh'''
                mvn -B -DskipTests clean package
                mvn test
                echo 'Testing and validating the code '
                sh'''
            }
        }
        stage('Atrifract'){
            steps{
                archiveArtifacts artifacts: '**/*.war'
                echo "Creating the Atrifact"
            }
        }
    }
    post {
        always {
            cleanWs()
        }
        success{
            echo 'Job is successful'
        }
        failure{
            echo 'Job is failed'
        }
    }
}
