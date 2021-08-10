pipeline {
    agent any
	tools { 
        maven 'MAVEN_HOME'  
		sonarqube 'SonarQube'
    }

    stages {
        stage('CompileandPackage') {
            steps {
				bat("mvn -Dmaven.test.failure.ignore clean compile")
			}
            
        }
		
		stage('SonarQube analysis') {
            steps {
                    bat( "mvn sonarqube")
            }
        }
		
		stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
        
    }
}