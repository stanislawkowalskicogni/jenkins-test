pipeline {
    agent any
    options{
        copyArtifactPermission("test123")
    }
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
    }
}