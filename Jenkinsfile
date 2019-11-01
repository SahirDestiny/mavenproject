pipeline {

   agent any


 
   stages {

      stage('Build') {

         steps {

            // Get some code from a GitHub repository

            git 'https://github.com/SahirDestiny/mavenproject.git'

            
	   // Run Maven on a Unix agent.
            
	    sh "mvn clean install package"

 
	    }           
	   post {
            
		// If Maven was able to run the tests, even if some of the test
                      
		success {
               
		junit '**/target/surefire-reports/TEST-*.xml'
               
		archiveArtifacts 'target/*.jar'
            
  		}

         }
      
	}
      }
   
}