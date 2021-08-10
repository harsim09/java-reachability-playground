pipeline {
    agent any
	tools { 
        maven 'MAVEN_HOME'  
    }

    stages {
	
			stage('SonarQube analysis') {
			ws("D:\Harsimran\Github\java-reachability-playground") {
			// requires SonarQube Scanner 2.8+
			def scannerHome = tool 'sonarqube scanner';
			bat "${scannerHome}/bin/sonar-scanner.bat"
		  }
		}
        stage('CompileandPackage') {
            steps {
				bat("mvn -Dmaven.test.failure.ignore clean compile sonar:sonar")
			}
            
        }
		
		stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
        
    }
}