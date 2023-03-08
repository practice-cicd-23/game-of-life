node('MAVEN_JDK_8') {
    stage('version control') {
        git url: 'https://github.com/practice-cicd-23/game-of-life.git',
            branch: 'pravin'
    }
    stage('build') {
        sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
    }
    stage('archive the artifacts') {
         archiveArtifacts onlyIfSuccessful: true,
            artifacts: '**/target/gameoflife.war',
            allowEmptyArchive: false
    }
    stage('show the test results') {
        junit testResults: '**/surefire-reports/TEST-*.xml',
              allowEmptyResults: true
    }
}