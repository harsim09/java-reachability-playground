pipeline {
    agent any
	tools { 
        maven 'Maven 3.3.9' 
        jdk 'jdk8' 
    }

    stages {
        stage('SetEnv') {
            steps {
				 sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }
        stage('CompileandPackage') {
            steps {
                withEnv(["M2_HOME=${M2_HOME}"]) {
				bat(/"%M2_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean compile/)
         }
            }
        }
        
    }
}