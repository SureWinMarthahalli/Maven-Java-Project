#!groovy

node {
    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){
	       
         sh 'export M3_HOME=/opt/Maven/apache-maven-3.5.3'
	 sh 'export PATH=$M3_HOME/bin:$PATH'

          sh 'mvn clean install'
	       }
	   
      stage('Sonar') {
	      
                    //add stage sonar
                    sh 'mvn sonar:sonar'
	      }
	    
	stage('Checkstyle') {
		
                    sh 'mvn checkstyle:checkstyle'
		}

               stage('PMD') {
		       
                    sh 'mvn pmd:check'
		       }
      /* stage('mail'){

         mail body: 'project build successful',
                     from: 'devopstrainingblr@gmail.com',
                     replyTo: 'mithunreddytechnologies@gmail.com',
                     subject: 'project build successful',
                     to: 'mithunreddytechnologies@gmail.com'
       }*/
	    
	    

    }
    catch (err) {

        currentBuild.result = "FAILURE"

           /* mail body: "project build error is here: ${env.BUILD_URL}" ,
            from: 'devopstrainingblr@gmail.com',
            replyTo: 'mithunreddytechnologies@gmail.com',
            subject: 'project build failed',
            to: 'mithunreddytechnologies@gmail.com'
            */
        throw err
    }
}
