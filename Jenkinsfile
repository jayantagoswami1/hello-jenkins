pipeline {
    agent any

    stages {

        stage('Environment Check') {
            steps {
                bat '''
                    echo ===== USER =====
                    whoami

                    echo ===== CURRENT DIRECTORY =====
                    cd

                    echo ===== JAVA =====
                    java -version

                    echo ===== MAVEN =====
                    mvn -version

                    echo ===== WORKSPACE CONTENT =====
                    dir

                    echo ===== POM CHECK =====
                    if exist pom.xml (
                        echo pom.xml FOUND
                    ) else (
                        echo ERROR: pom.xml NOT FOUND
                        exit /b 1
                    )
                '''
            }
        }

        stage('Publish to Exchange') {
            steps {
                bat 'mvn clean deploy'
            }
        }

        stage('Deploy to CloudHub 2.0') {
            steps {
                bat 'mvn clean deploy -DmuleDeploy'
            }
        }
    }
}