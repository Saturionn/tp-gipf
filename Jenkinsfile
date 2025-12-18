pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Compilation') {
            steps {
                sh './gradlew -D https.proxyHost=proxy1-rech.uphf.fr -D https.proxyPort=3128 compileJava'
            }
        }
      stage('Test'){
        steps{
          sh './gradlew -D https.proxyHost=proxy1-rech.uphf.fr -D https.proxyPort=3128 test'
        }
      }
      stage('SonarQube'){
        steps{
            sh "./gradlew sonar -Dsonar.projectKey=tp-gipf -Dsonar.projectName='tp-gipf' -Dsonar.host.url=http://172.17.0.1:9000 -Dsonar.token=sqp_c24749618b1e0a155a699ce6df374e5168020b1c"
        }
      }
      stage('Jar'){
        steps{
          sh "./gradlew -D https.proxyHost=proxy1-rech.uphf.fr -D https.proxyPort=3128 jar"
          archiveArtifacts artifacts: 'build/libs/*.jar'
        }
      }
    }
}
