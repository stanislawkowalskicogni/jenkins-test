pipeline {
    agent {
        node {
            label "${whichNodes}"
        }
    }
    properties([copyArtifactPermission("test123")])
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
    }
}