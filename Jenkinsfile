pipeline {
    agent {
        docker {
            image 'maven:3.8.8-eclipse-temurin-17-alpine'
        }
    }
   // tools {
   //     maven 'maven3.8.8'
    //}
    stages {
      //  stage('Checkout SCM') {
       //     steps {
         //       git branch: 'master', url:'https://github.com/nrobles2013/spring-petclinic-rest'
           //     sh 'ls -la'
            //}
       // }
        stage('Compile') {
            steps {
                sh 'mvn clean compile -B -ntp'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test -B -ntp'
                junit 'target/surefire-reports/*.xml'
                jacoco()
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package -B -ntp'
            }
        }
    }
}
