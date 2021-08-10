pipeline {
    agent any
	tools { 
        maven 'MAVEN_HOME'  
    }

    stages {
		
		
        stage('CompileandPackage') {
            steps {
			
				bat("mvn -Dmaven.test.failure.ignore clean compile sonar:sonar -Dsonar.login=64ff722206f9599e63b429194cda2239d673c5fa -Dsonar.projectKey=github-jenkins-java-sonar -Dsonar.host.url=http://localhost:9000/")
			
            
			}
        }
		
        
    }
}