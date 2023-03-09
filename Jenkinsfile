pipeline {
    agent { label 'MAVEN_JDK_8' }
    triggers { pollSCM ('H/30 * * * *') }
    parameters {
        string(name: 'MAVEN_GOAL', defaultValue: 'package', description: 'MAVEN GOAL')
    } 
    stages {
        stage('vsc') {
            steps {
                git url: 'https://github.com/practice-cicd-23/game-of-life.git',
                    branch: 'declrative'
            }
        
        }
        stage('package') {
            steps {
                sh "mvn ${params.MAVEN_GOAL}"
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