pipeline {
    agent any
 
    environment {
	ENV_BUILD_NO = "${env.BUILD_NUMBER}"
	JENKINS_URL = "${env.JENKINS_URL}"
	JOB_NAME = "${env.JOB_NAME}"
	JENKINS_HOME = "${env.JENKINS_HOME}"
	GIT_BRANCH =    "${env.GIT_BRANCH}" 
    }
   
   stages {
      	   
		   stage ('Build only on master') {
          
			 when { branch 'master' }
				steps { 
					echo 'I only execute on the master branch.' 
									
				echo ENV_BUILD_NO
                echo JENKINS_URL
                echo JOB_NAME
                echo JENKINS_HOME
                echo 'Stage Run'
				echo GIT_BRANCH

										
						}
										}
					
		stage ('Test 3: Dev') {
				when { not { branch 'Maven-Build' } }
					steps {
					echo 'I execute on non-master branches.'
					echo ENV_BUILD_NO
					echo JENKINS_URL
					echo JOB_NAME
					echo JENKINS_HOME
					echo 'Stage Run'
					echo GIT_BRANCH
				}
							}					
										
										
		   
        }
      

   
	  post{
   
   always{
   
   				echo 'Report Mail sending'
            script {
                    emailext subject: '$DEFAULT_SUBJECT'+ GIT_BRANCH,    
			body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:' ,
                        attachLog: true,
                        replyTo: '$DEFAULT_REPLYTO',
                        to: 'pranav@techvision.net.in'
            }
   }
   
}
	
	
}
