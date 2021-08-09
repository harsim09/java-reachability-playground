	1) Install Sonarqube on local system and 
	
	Open SonarQube server- Go to Administration > click on Security > Users > Click on Tokens (image 1)> Generate token with some name > Copy the token (image 2), it will be used in Jenkins for Sonar authentication
	
	From <https://medium.com/@amitvermaa93/jenkins-sonarqube-integration-129f5c49c4ca> 
	
	
	2) Install Jenkins and

	Go to Manage Jenkins > Configure system > SonarQube server section > Add SonarQube > Name it, provide Server Url as http://<IP>:<port> > and authentication token copied from SonarQube Server > Apply and Save
	
	From <https://medium.com/@amitvermaa93/jenkins-sonarqube-integration-129f5c49c4ca> 
	
	
	3) Install SonarQube plugin to Jenkins. Go to Manage Jenkins > Manage Plugins > Available > Search for SonarQube Scanner> Install
	
	From <https://medium.com/@amitvermaa93/jenkins-sonarqube-integration-129f5c49c4ca> 

	4) Download SonarScanner if you don’t  have  https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner
	
	From <https://medium.com/@amitvermaa93/jenkins-sonarqube-integration-129f5c49c4ca> 
	
	Or Configure Sonar Scanner in Jenkins : Go to Mange Jenkins > Global Tool Configuration > Scroll for SonarQube Scanner > Add sonar scanner > name it, uncheck if you already have sonar else it will automatically download for you and your sonar scanner setup will be done
	
	From <https://medium.com/@amitvermaa93/jenkins-sonarqube-integration-129f5c49c4ca> 
	
	By install automatically
	
	
	5) Create Sonarqube.properties file and place it in project with following details:

# must be unique in a given SonarQube instance
sonar.projectKey=github-jenkins-java-sonar

# --- optional properties ---

# defaults to project key
#sonar.projectName=My project
# defaults to 'not provided'
#sonar.projectVersion=1.0
 
# Path is relative to the sonar-project.properties file. Defaults to .
sonar.projectVersion=1.0
sonar.sources=./src/main/java/
sonar.language=java
sonar.java.binaries=./target/classes 
 
# Encoding of the source code. Default is default system encoding
#sonar.sourceEncoding=UTF-8


	6) Configure maven job with jenkins 


	
	
	
	
	
