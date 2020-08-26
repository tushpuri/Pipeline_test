pipeline {  
	agent any
	
	stages {
		stage('Build Application') {
	        	steps {
				echo 'Build Appplication...' 
	                	bat 'mvn clean install'
			}
		}
	        stage('Test') {
	               steps {
	                  	echo 'Test Appplication...' 
        		  	//bat 'mvn clean test'      
        		}   
		}
               stage('Deploy CloudHub') {
		       environment {
                		ANYPOINT_CREDENTIALS = credentials('Anypoint_Studio')
            		}
		       steps {
			       echo 'Deploying only because of code commit...'
			       echo "Username is $ANYPOINT_CREDENTIALS_USR"
			       bat "mvn package deploy -DmuleDeploy -DskipMunitTests -Danypoint.environment=Sandbox -Danypoint.username=$ANYPOINT_CREDENTIALS_USR -Danypoint.password=$ANYPOINT_CREDENTIALS_PSW -Danypoint.workers=1 -Danypoint.workersType=MICRO -Danypoint.applicationName=Hello-Application-3 -Danypoint.muleVersion=4.3.0 -DobjectStoreV2=true"
		       }    
	       }  
	}
}
