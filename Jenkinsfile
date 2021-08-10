pipeline {
    agent any
	tools { 
        maven 'MAVEN_HOME'  
    }

    stages {
			stage('Build') {
			environment{
			 scannerHome = tool 'sonarqube scanner'
			}
            steps {
                    bat("${scannerHome}/bin/sonar-scanner")
                
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