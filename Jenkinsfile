pipeline {
    agent any
    options{
        copyArtifactPermission("jenkins-copy-test")
    }
    stages {
        stage('build') {
            steps {
                echo 'after1'
                bat './gradlew build --no-daemon'
                echo 'before1'
            }
        }
        stage('archive') {
            steps {
                echo 'after2'
                archiveArtifacts artifacts: '/build/libs/*.jar*', allowEmptyArchive: false, onlyIfSuccessful: true
                echo 'before2'
            }
        }
        stage('trigger build') {
            steps {
                echo URLDecoder.decode(env['BRANCH_NAME'], "UTF-8")
                build job: 'jenkins-copy-test',
                        parameters: [string(name: 'BRANCH_NAME', value: URLDecoder.decode(env['BRANCH_NAME'], "UTF-8").replaceAll("/", "-")),
                                     string(name: 'SNAPSHOT_NAME', value: 'SNAPSHOT')],
                        propagate: false,
                        quietPeriod: 30
            }
        }
    }
}