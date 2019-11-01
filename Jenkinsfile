pipeline {

   agent any

   tools {
      
	// Install the Maven version configured as "M3" and add it to the path.
      
	maven 'maven-3.6.2'
	jdk 'java8'
	}
 
 
   stages {

      stage('Build') {

         steps {

            // Get some code from a GitHub repository

            git 'https://github.com/SahirDestiny/mavenproject.git'

            
	   // Run Maven on a Unix agent.
            
	    sh "mvn clean install package"

 
	    }
	}
      stage ('Deploy'){
	steps{
	    deploy adapters: [tomcat8(credentialsId: 'b499ca1c-331a-4290-9e7e-dab543d4dd2c', path: '', url: 'http://13.235.78.19:8080/')], contextPath: 'webapp.war', war: '**/*.war'

	     }
         }  
      }   
	   post {
                               
		success {
               
		junit '**/target/surefire-reports/TEST-*.xml'
               
		}

             }
            
   
}