pipeline {
    agent any

    options{
        copyArtifactPermission("copy-from-jenkins-test")
    }
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
    }
}