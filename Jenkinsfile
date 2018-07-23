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
                    stage('test') {
                            steps {
                                    sh 'echo hello'
                            }
                    }
                    stage('test1') {
                            steps {
                                    sh 'echo $TEST'
                            }
                    }
                    stage('test3') {
                            steps {
                                    script {
                                            if (GIT_BRANCH == 'origin/master') {
                                                    echo 'I only execute on the master branch'
                                            } else {
                                                    echo 'I execute elsewhere'
                                            }
					    
                                    }
                            }
                    }
            }
      

	
   }
   
	  post{
   
   always{
   
   				echo 'Report Mail sending'
        //    script {
        //            emailext subject: '$DEFAULT_SUBJECT'+ GIT_BRANCH,    
		//	body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:' ,
        //                attachLog: true,
        //               replyTo: '$DEFAULT_REPLYTO',
        //                to: 'pranav@techvision.net.in'
        //    }
   }
   
}
	
	

