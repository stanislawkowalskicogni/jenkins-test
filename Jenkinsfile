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
        stage('archive') {
            steps {
                archiveArtifacts artifacts: '*.jar*', allowEmptyArchive: false, onlyIfSuccessful: true
            }
        }
    }
}