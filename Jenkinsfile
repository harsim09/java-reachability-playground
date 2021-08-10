pipeline {
    agent any
	tools { 
        maven 'MAVEN_HOME'  
    }

    stages {
        stage('CompileandPackage') {
            steps {
				bat("mvn -Dmaven.test.failure.ignore clean compile")
			}
            
        }
		
		stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat( "mvn sonarqube")
                }
            }
        }
		
		stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
        
    }
}