pipeline {
    agent { label 'MAVEN_JDK_8' }  
    stages {
        stage('vsc') {
            steps {
                 git url: 'https://github.com/practice-cicd-23/game-of-life.git',
                     branch: 'declrative'
            }
        
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
    }
}