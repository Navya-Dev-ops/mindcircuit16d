pipeline {

    agent any
    stages {
	
        stage('CLONE SCM') {
            steps {
                echo 'This stage clones SC from GIT repo'				
				git branch: 'main', url: 'https://github.com/Navya-Dev-ops/mindcircuit16d.git'
            }
        }
		
        stage('Build Artifact') {
            steps {
                echo 'This stage builds the code using maven'
				sh 'mvn clean install'			
				
            }
        }
		
       stage('Deploy to Tomcat') {
            steps {
                echo 'This stage deploys .war to tomcat webserver'
             deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://ec2-18-207-116-83.compute-1.amazonaws.com:8080/')], contextPath: 'MC-PIPELINE', war: '**/*.war'
            }
        }		
		
    }
}
