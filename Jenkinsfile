pipeline{

      agent {
                any {
                image 'maven:3-openjdk-11'
			tools {
				 maven 'Maven 3.8.6'
        jdk 'Java 17.0.4.1'}

                }
            }
        
        stages{

              stage('Quality Gate Status Check'){
                  steps{
                      script{
			      withSonarQubeEnv('sonarserver') { 
			      sh "mvn clean sonar:sonar"
                       	     	}
			      timeout(time: 1, unit: 'HOURS') {
			      def qg = waitForQualityGate()
				      if (qg.status != 'OK') {
					   error "Pipeline aborted due to quality gate failure: ${qg.status}"
				      }
                    		}
		    	    sh "mvn clean install"
		  
                 	}
               	 }  
              }	
		
            }	       	     	         
}


 maven 'Maven 3.8.6'
        jdk 'Java 17.0.4.1'
