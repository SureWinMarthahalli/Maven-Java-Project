#!groovy

node {
    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){
	       steps{
	       withMaven(maven : 'maven 3.5.3')

          sh 'mvn clean install'
	       }}
	   
      stage('Sonar') {
	      steps{
	       withMaven(maven : 'maven 3.5.3')
                    //add stage sonar
                    sh 'mvn sonar:sonar'
	      }}
	    
	stage('Checkstyle') {
		steps{
	       withMaven(maven : 'maven 3.5.3')
                    sh 'mvn checkstyle:checkstyle'
		}}

               stage('PMD') {
		       steps{
	       withMaven(maven : 'maven 3.5.3')
                    sh 'mvn pmd:check'
		       }}
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
