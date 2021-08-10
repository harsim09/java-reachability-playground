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
			script{
			withSonarQubeEnv('sonarqubetest'){
				bat("mvn -Dmaven.test.failure.ignore sonar:sonar -Dsonar.login=admin -Dsonar.password=Ikonkar@10 -Dsonar.projectKey=github-jenkins-java-sonar -Dsonar.host.url=http://localhost:9000/")
			}
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