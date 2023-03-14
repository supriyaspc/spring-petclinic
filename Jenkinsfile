node('MAVEN_JDK8') {
    stage('version control') {
        git url: 'https://github.com/supriyaspc/spring-petclinic.git',
            branch: 'declarative'
    }
    stage: ('build the code') {
        sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
    }
    stage('archive the artifacts') {
        archiveArtifacts onlyIfSuccessful: true 
        artifacts: '**/target/springpeclinic.txt',
        allowEmptyArchive: false,

    }
    stage('shoe the test results')
    junit testResults: '**/build/test-reports/*.xml',
    allowEmptyResults: true,

}