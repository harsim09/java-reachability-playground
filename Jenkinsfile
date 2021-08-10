pipeline {
    agent any

    stages {
        stage('SetEnv') {
            steps {
				mvnHome = tool 'MAVEN_HOME'
            }
        }
        stage('CompileandPackage') {
            steps {
                withEnv(["MVN_HOME=$mvnHome"]) {
				bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean compile/)
         }
            }
        }
        
    }
}