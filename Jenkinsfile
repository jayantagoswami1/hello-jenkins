groovy
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
