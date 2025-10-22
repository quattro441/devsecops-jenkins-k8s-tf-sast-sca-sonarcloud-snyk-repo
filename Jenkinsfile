pipeline {
  agent any
  tools { 
        maven 'maven_3_9_11'  
    }
   stages{
/*    THIS IS THE ORIGINAL CODE
		stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=asgbuggywebapp -Dsonar.organization=asgbuggywebapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=932558e169d66a8f1d1adf470b908a46156f5844'
			}
    }
*/	   
	    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=quattrosec_buggywebapp -Dsonar.organization=quattrosec -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=6b0defa2e7880e6b125cb848dfe9ff3917a5d1f0'
			}
    }   
	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
