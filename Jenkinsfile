pipeline{
    agent {
        docker {
            image 'circleci/android'
        }
    }
    stages {
        stage('Build'){
             steps {
                sh './gradlew clean && rm -rf ./app/build/'
                sh './gradlew assembleRelease'
             }
        }
       stage('UnitTest'){
             steps {
                sh './gradlew test'
             }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'app/build/outputs/**/*.apk', fingerprint: true
            }
        }
    }

}