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
        stage('sonar analysis') {
            steps {
                sh 'mvn clean verify sonar:sonar \
                    -Dsonar.login=eb9a16c5f210a865af89438c0330155a4714c311 \
                    -Dsonar.host.url=https://sonarcloud.io \
                    -Dsonar.projectKey=spc-sonar \
                    -Dsonar.organization=spc-sonar'
           }
        }
    }
}
