pipeline {
    agent any
 
    environment {
    ENV_NAME = "${env.BRANCH_NAME}"
	ENV_BUILD_NO = "${env.BUILD_NUMBER}"
	JENKINS_URL = "${env.JENKINS_URL}"
	JOB_NAME = "${env.JOB_NAME}"
	JENKINS_HOME = "${env.JENKINS_HOME}"
	GIT_COMMIT = "${env.GIT_COMMIT}"
	GIT_BRANCH =    "${env.GIT_BRANCH}" 
    }
   
   stages {
      
           stage ('Stage Run') {

            steps {    
                echo ENV_BUILD_NO
                echo JENKINS_URL
                echo JOB_NAME
                echo JENKINS_HOME
               echo 'Stage Run'
		    echo GIT_BRANCH
		    echo GIT_COMMIT
                echo ENV_NAME
            }
        }
      
   }
   
}
