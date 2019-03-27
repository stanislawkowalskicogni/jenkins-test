pipeline {
    agent any
//    options{
//        copyArtifactPermission("jenkins-copy-test")
//    }
    stages {
        stage('build') {
            steps {
                bat './gradlew build --no-daemon'
            }
        }
        stage('archive') {
            steps {
                archiveArtifacts artifacts: '/build/libs/*.jar*', allowEmptyArchive: false, onlyIfSuccessful: true
            }
        }
        stage('trigger build') {
            steps {
                echo URLDecoder.decode(env['BRANCH_NAME'], "UTF-8")
                build job: 'jenkins-copy-test',
                        parameters: [string(name: 'BRANCH_NAME', value: URLDecoder.decode(env['BRANCH_NAME'], "UTF-8").replaceAll("/", "-")),
                                     string(name: 'SNAPSHOT_NAME', value: 'SNAPSHOT')],
                        propagate: false
            }
        }
    }
}