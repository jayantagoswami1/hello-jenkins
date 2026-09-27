pipeline {
    agent any

    stages {

        stage('Run MUnit Tests') {
            steps {
                bat 'mvn -s "C:\\Users\\07622I744\\.m2\\settings.xml" clean test'
            }
        }

        stage('Publish to Exchange') {
            steps {
                bat 'mvn -s "C:\\Users\\07622I744\\.m2\\settings.xml" clean deploy'
            }
        }

        stage('Deploy to CloudHub 2.0') {
            steps {
                bat 'mvn -s "C:\\Users\\07622I744\\.m2\\settings.xml" clean deploy -DmuleDeploy'
            }
        }
    }
}