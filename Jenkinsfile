pipeline {
    agent {
        node {
            properties([$class: 'CopyArtifactPermissionProperty', projectNames: 'jlr-odyssey-xmetal-cust-release'])
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