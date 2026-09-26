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
        
        ```groovy
	stage('Maven Configuration Check') {
	    steps {
	        bat '''
	            echo ==============================
	            echo WINDOWS USER
	            echo ==============================
	            whoami
	
	            echo ==============================
	            echo USERPROFILE
	            echo ==============================
	            echo %USERPROFILE%
	
	            echo ==============================
	            echo MAVEN
	            echo ==============================
	            mvn -version
	
	            echo ==============================
	            echo MAVEN SETTINGS
	            echo ==============================
	            if exist "%USERPROFILE%\\.m2\\settings.xml" (
	                echo settings.xml EXISTS
	            ) else (
	                echo settings.xml DOES NOT EXIST
	            )
	
	            echo ==============================
	            echo CONNECTED APP SERVER CHECK
	            echo ==============================
	            if exist "%USERPROFILE%\\.m2\\settings.xml" (
	                findstr /I "<id>connectedApp</id>" "%USERPROFILE%\\.m2\\settings.xml"
	            ) else (
	                echo No settings.xml found
	            )
	        '''
	    }
	}
```

        stage('Publish to Exchange') {
    steps {
        bat '''
            mvn -s "C:\\Users\\07622I744\\.m2\\settings.xml" clean deploy
        '''
    }
}

        stage('Deploy to CloudHub 2.0') {
            steps {
                bat 'mvn clean deploy -DmuleDeploy'
            }
        }
    }
}