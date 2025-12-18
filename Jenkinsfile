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
          sh './gradlew sonar -Dsonar.projectKey=tp-gipf -Dsonar.projectName='tp-gipf' -Dsonar.host.url=http://172.17.0.1:9000 -Dsonar.token=squ_6a0db0100a8efa78de09262e31721e2022272195'
        }
      }
      stage('Jar'){
        steps{
          sh "./gradlew jar"
          archiveArtifacts artifacts: 'build/libs/*.jar'
        }
      }
