pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git 'https://github.com/Sanchay1054/WarProject.git'
            }
        }
        stage('build') {
            steps {
               bat "mvn clean"
               bat "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  bat 'docker build -t sanchaym/simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'Docker', url: 'https://index.docker.io/v1/') {
                  bat 'docker push sanchaym/simplewebapp'
               }
            }
 	}
}
}
}