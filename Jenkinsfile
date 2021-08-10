pipeline {
    agent any
	tools { 
        maven 'MAVEN_HOME'  
    }

    stages {
        stage('SetEnv') {
            steps {
				 sh '''
                    echo "PATH = ${PATH}"
                    echo "MAVEN_HOME = ${MAVEN_HOME}"
                ''' 
            }
        }
        stage('CompileandPackage') {
            steps {
                withEnv(["MAVEN_HOME=${MAVEN_HOME}"]) {
				bat(/"%MAVEN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean compile/)
         }
            }
        }
        
    }
}