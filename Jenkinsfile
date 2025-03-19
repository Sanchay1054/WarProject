pipeline {
    agent any
tools {maven 'mvn'}

    stages {
        stage('scm') {
            steps {
        git 'https://github.com/Sanchay1054/WarProject.git'
            }
        }
        stage('build') {
            steps {
               sh "mvn clean"
               sh "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  sh 'docker build -t sanchaym/simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'docker', url: 'https://index.docker.io/v1/') {
                  sh 'docker push sanchaym/simplewebapp'
               }
            }
 	}
}
}
}