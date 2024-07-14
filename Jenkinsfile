pipeline {
    agent any
    tools {
        maven 'maven3.8.8'
    }
    stages {
      //  stage('Checkout SCM') {
       //     steps {
         //       git branch: 'master', url:'https://github.com/nrobles2013/spring-petclinic-rest'
           //     sh 'ls -la'
            //}
       // }
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests -B -ntp'
            }
        }
    }
}
