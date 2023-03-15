pipeline {
    agent { label 'MAVEN_PEM' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/supriyaspc/spring-petclinic.git',
                    branch: 'develop'
            }
        } 
        stage('package') {
            steps {
                sh './mvnw package' 
            }
        } 
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
        stage('craeting folder') {           
            steps {
                sh "mkdir -p /tmp/archive/spring-petclinic"
                sh "cp -r */spring-petclinic-*.jar /tmp/archive/spring-petclinic"
                sh " sudo aws s3 sync /tmp/archive/spring-petclinic s3://awsbucket0319 --acl public-read-write"
            }
        }
    }
}
