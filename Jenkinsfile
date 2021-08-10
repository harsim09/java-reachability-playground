pipeline {
    agent any
	tools { 
        maven 'MAVEN_HOME'  
    }

    stages {
	
			stage('SonarQube analysis') {
			steps{
				script {
				scannerHome = tool 'sonarqube scanner';
			}
			withSonarQubeEnv('SonarQube') {
            bat "${scannerHome}/bin/sonar-scanner.bat" 
			}
			}
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