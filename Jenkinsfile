pipeline {
    agent any
    triggers {
       pollSCM('*/2 * * * *')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh './gradlew wrapper
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
}
