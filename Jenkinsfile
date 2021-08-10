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
				bat("mvn -Dmaven.test.failure.ignore clean compile sonar:sonar -Dsonar.login=6f2c9fb6c4546e8327f3471c0a50c97b17f4a622")
			}
            
        }
		
		stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
        
    }
}