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
                sh './gradlew compileJava'
            }
        }
      stage('Test'){
        steps{
          sh './gradlew test'
        }
      }
      stage('SonarQube'){
        steps{
            sh './gradlew sonar -Dsonar.projectKey=tp-gipf -Dsonar.projectName='tp-gipf' -Dsonar.host.url=http://127.17.0.1:9000 -Dsonar.token=sqp_c24749618b1e0a155a699ce6df374e5168020b1c'
        }
      }
      stage('Jar'){
        steps{
          sh "./gradlew jar"
          archiveArtifacts artifacts: 'build/libs/*.jar'
        }
      }
    }
}
