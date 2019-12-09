pipeline {
    agent any
    triggers {
       pollSCM('*/2 * * * *')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh './gradlew clean assemble'
		            archiveArtifacts 'build/libs/*.jar'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh './gradlew clean test'
		            junit 'build/test-results/test/*.xml'
            }
        }
    } 
}
