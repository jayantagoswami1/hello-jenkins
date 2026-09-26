pipeline {
agent any

```
stages {

    stage('Maven Configuration Check') {
        steps {
            bat '''
                echo ==============================
                echo USER
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
                echo SETTINGS FILE
                echo ==============================
                if exist "%USERPROFILE%\\.m2\\settings.xml" (
                    echo settings.xml EXISTS
                    echo.
                    echo Checking connectedApp:
                    findstr /I "connectedApp" "%USERPROFILE%\\.m2\\settings.xml"
                ) else (
                    echo settings.xml DOES NOT EXIST
                )

                echo ==============================
                echo MAVEN EFFECTIVE SETTINGS
                echo ==============================
                mvn help:effective-settings -DshowPasswords=false
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
```

}
