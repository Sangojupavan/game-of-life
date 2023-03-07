pipeline {
    agent { label 'JDK_8' }
    stages {
        stage ('vcs') {
            steps {
                git url: 'https://github.com/Sangojupavan/game-of-life.git',
                    branch: 'declarative'
            }
        }
        stage ('package') {
            steps {
                sh 'mvn package'
            }
        }
        stage ('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'               

            }
        }
    }
       
}
