pipeline {
    agent any
	tools { 
        maven 'MAVEN_HOME'  
		sonar 'SonarQube'
    }

    stages {
        stage('CompileandPackage') {
            steps {
				bat("mvn -Dmaven.test.failure.ignore clean compile")
			}
            
        }
		
		stage('SonarQube analysis') {
            steps {
                    bat( "mvn sonar")
            }
        }
		
		stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
        
    }
}