pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'war', url: 'https://github.com/awspandian/oct26.git'
            }
        }
	stage('BUILD') {
            steps {
                bat 'mvn clean'
		bat 'mvn install'
            }
        }
	stage('Deploy') {
            steps {
               deploy adapters: [tomcat9(credentialsId: 'web', path: '', url: 'http://localhost:9090/')], contextPath: 'pipe', war: '**/*.war'
            }
        }

    }
}
