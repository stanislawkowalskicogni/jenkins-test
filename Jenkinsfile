pipeline {
    agent {
        node {
            properties([copyArtifactPermission("test123")])
            label "${whichNodes}"
        }
    }
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
    }
}