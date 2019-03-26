pipeline {
    agent {
        node {
            properties(copyArtifactPermission("test123"))
            label "${whichNodes}"
        }
    }
    properties([$class: 'CopyArtifactPermissionProperty', projectNames: 'jlr-odyssey-xmetal-cust-release'])
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
    }
}