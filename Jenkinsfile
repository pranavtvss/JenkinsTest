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
					echo 'Result of previous build' + currentBuild.getPreviousBuild().result
					echo 'Env build number' +ENV_BUILD_NO
					echo 'Jenkins URL' +JENKINS_URL
					echo 'JOB NAME' +JOB_NAME
					echo 'JENKINS HOME' +JENKINS_HOME
					echo 'GIT BRANCH' +GIT_BRANCH				
				

										
						}
										}
					
		stage ('Build only on non-master') {
				when { not { branch 'master' } }
					steps {
					echo 'I execute on non-master branches.'
					echo 'Result of previous build' + currentBuild.getPreviousBuild().result
					echo 'Env build number' +ENV_BUILD_NO
					echo 'Jenkins URL' +JENKINS_URL
					echo 'JOB NAME' +JOB_NAME
					echo 'JENKINS HOME' +JENKINS_HOME
					echo 'GIT BRANCH' +GIT_BRANCH
				}
							}					
										
										
		   
        }
      

   
	  post{
   
   always{
   
   				echo 'Report Mail sending'
   //         script {
   //                 emailext subject: '$DEFAULT_SUBJECT'+ GIT_BRANCH,    
//			body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:' ,
   //                     attachLog: true,
   //                     replyTo: '$DEFAULT_REPLYTO',
   //                     to: 'pranav@techvision.net.in'
   //         }
   }
   
}
	
	
}
