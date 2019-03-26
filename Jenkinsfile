pipeline {
    agent {
        node {
            label "${whichNodes}"
        }
    }
    options([copyArtifactPermission("test123")])
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
    }
}