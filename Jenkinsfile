pipeline {
    agent { label 'MAVEN_JDK_8' }
    triggers { cron('H/15 * * * *') }  
    stages {
        stage('vsc') {
            steps {
                git url: 'https://github.com/practice-cicd-23/game-of-life.git',
                    branch: 'declrative'
            }
        
        }
        stage('package') {
            steps {
                sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}