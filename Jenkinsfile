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
        stage('Archive XMetal Resources') {
            steps {
                archiveArtifacts artifacts: archivesLocation + '/*.jar*', allowEmptyArchive: false, onlyIfSuccessful: true
            }
        }
    }
}