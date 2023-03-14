node('MAVEN_JDK8') {
    stage('version control') {
        tools {
            jdk 'JDK-17'
        }
        git url: 'https://github.com/supriyaspc/spring-petclinic.git',
            branch: 'scripted'
    }
}