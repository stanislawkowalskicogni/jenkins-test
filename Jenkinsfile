pipeline {
    agent any
    properties([$class: 'CopyArtifactPermissionProperty', projectNames: 'jlr-odyssey-xmetal-cust-release'])
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
    }
}