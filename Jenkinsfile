pipeline {
    agent any
    triggers {
       pollSCM('*/2 * * * *')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh './gradlew wrapper'
                sh './gradlew build'
		            
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh './gradlew test'
		           
            }
        }
    }
    post {
      success {
        mail to: "alanescalera.english@gmail.com",
        subject:"SUCCESS: ${currentBuild.fullDisplayName}",
        body: "Result: ${currentBuild.result}\
         Job: ${env.JOB_NAME}\
         Build: ${env.BUILD_NUMBER}\
         URL: ${env.BUILD_URL}"
      }
      failure {
        mail to: "alanescalera.english@gmail.com",
        subject:"FAILURE: ${currentBuild.fullDisplayName}",
        body: "Result: ${currentBuild.result}\
         Job: ${env.JOB_NAME}\
         Build: ${env.BUILD_NUMBER}\
         URL: ${env.BUILD_URL}"
      }
    } 
}
