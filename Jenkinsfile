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
        }
        
    }
}