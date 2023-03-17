pipeline {
    agent { label 'MAVENPEM' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/supriyaspc/spring-petclinic.git',
                    branch: 'develop'
            }
        }
        stage('package') {
            steps {
                sh 'mvn package'
            }
        } 
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar',
                   allowEmptyArchive: true,
                   fingerprint: true,
                   onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}