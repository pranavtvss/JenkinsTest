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
           
            }
        }
      
   }
   
	  post{
   
   always{
   
   				echo 'Report Mail sending'
            script {
                    emailext subject: '$DEFAULT_SUBJECT'+ GIT_BRANCH + GIT_COMMIT,    
			body: "Click the link below to show REST API Testing Results for your current build :  \n"+JENKINS_URL+"blue/organizations/jenkins/"+JOB_NAME+"/detail/"+JOB_NAME+"/activity/"+"\n\n\n Click the link below to show Mockito TestNG Results for your current build :  \n"+" https://bwrestapiqa.boardwalktech.com:8443/jenkins/userContent/"+JOB_NAME+"/Mockito_Reports/"+ENV_BUILD_NO+"/index.html" +"\n\n\n Click the link below to show Unit Testing Results for your current build :  \n"+" https://bwrestapiqa.boardwalktech.com:8443/jenkins/userContent/"+JOB_NAME+"/Unit_Reports/"+ENV_BUILD_NO+"/index.html" ,
                        attachLog: true,
                        replyTo: '$DEFAULT_REPLYTO',
                        to: 'pranav@techvision.net.in'          	
            }
   }
   
   }
	
	
}
