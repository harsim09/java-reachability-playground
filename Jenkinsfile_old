node{
    def mvnHome
 
   stage('SetEnv') { 
      git 'https://github.com/sneha0302/java-reachability-playground.git'
      mvnHome = tool 'MAVEN_HOME'
	   
   }
   
   stage('CompileandPackage') {
      withEnv(["MVN_HOME=$mvnHome"]) {
            bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean compile/)
         }
      
   }
   stage('Snyk'){
        snykSecurity failOnIssues: true, organisation: 'b398e91b-bba0-44d5-bd7a-d72d389e5cec', snykInstallation: 'SnykSec', snykTokenId: 'snykKey'
       
   }

}
