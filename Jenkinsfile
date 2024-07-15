pipeline {
    agent none
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
            agent {
                docker {
                    image 'maven:3.8.8-eclipse-temurin-17-alpine'
                }
            }
            steps {
                sh 'mvn clean compile -B -ntp'
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'maven:3.8.8-eclipse-temurin-17-alpine'
                }
            }
            steps {
                sh 'mvn test -B -ntp'
                junit 'target/surefire-reports/*.xml'
                jacoco()
                script{
                    var coverage = jacoco(execPattern: 'target/jacoco.exec',classPattern: '**/target/classes/java/main',sourcePattern:'**/target/*')
                }
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'maven:3.8.8-eclipse-temurin-17-alpine'
                }
            }
            steps {
                sh 'mvn package -B -ntp'
            }
        }
    }
}
