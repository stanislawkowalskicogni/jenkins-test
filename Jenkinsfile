pipeline {
    agent any

    options{
        copyArtifactPermission("jenkins-copy-test")
    }
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
    }
}