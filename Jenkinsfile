final String branchName = URLDecoder.decode(env['BRANCH_NAME'], "UTF-8")

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
                build job: 'jenkins-copy-test',
                        parameters: [string(name: 'BRANCH_NAME', value: branchName.replaceAll("/", "-")),
                                     string(name: 'SNAPSHOT_NAME', value: 'SNAPSHOT')],
                        propagate: false
            }
        }
    }
}