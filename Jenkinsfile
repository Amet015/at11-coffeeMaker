pipeline {
    agent any
    triggers {
       pollSCM('*/2 * * * *')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                bat './gradlew clean assemble'
		            archiveArtifacts 'build/libs/*.jar'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                bat './gradlew clean test'
		            junit 'build/test-results/test/*.xml'
            }
        }
    } 
}
