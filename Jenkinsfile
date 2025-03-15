pipeline {
    agent any

    stages {
        stage('clone Git Repo') {
            steps {
                echo 'clone the data from git repo'
               git branch: 'main', url: 'https://github.com/Swetha235/mindcircuit15d.git'
            }
        }

   stage('build war artifact') {
            steps {
                echo 'build war artifact using maven build tool'
               sh 'mvn clean install'
             }
          }

 stage('deploy app to tomcat') {
            steps {
                echo 'deploy war atifact on tomcat'
               deploy adapters: [tomcat9(credentialsId: '793e627c-ff33-4d97-9c4b-3af05b02ed29', path: '', url: 'http://ec2-3-90-66-197.compute-1.amazonaws.com:8081/')], contextPath: 'swethanetflix', war: '**/*.war'
             }
         }

    }
}
