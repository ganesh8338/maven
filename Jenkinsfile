pipeline {
    agent any
    
    tools {
        maven  'MAVEN'
    }
    
    stages {
    	 
	//    stage ('Clone') {
    //         steps {
    //             git branch: 'master', url: "https://github.com/abdallawi/07-jenkins-maven-plugin-01-unit-and-integration-tests.git"
    //         }
	//     }
	 
	   stage ('Build & Unit test'){
		    steps {
				sh 'mvn clean verify -DskipITs=true';
		      	junit '**/target/surefire-reports/TEST-*.xml'
		      	archiveArtifacts  'target/*.jar'
			}
   	    }
	
	   stage ('Integration Test'){
	        steps {
    			sh  'mvn clean verify -Dsurefire.skip=true';
				junit '**/target/failsafe-reports/TEST-*.xml'
      			archiveArtifacts  'target/*.jar'
      		}
        }	
    }
}
