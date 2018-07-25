pipeline {
    agent any

	
    environment {
	ENV_BUILD_NO = "${env.BUILD_NUMBER}"
	JENKINS_URL = "${env.JENKINS_URL}"
	JOB_NAME = "${env.JOB_NAME}"
	JENKINS_HOME = "${env.JENKINS_HOME}"
	GIT_BRANCH =    "${env.GIT_BRANCH}" 
	CODE_EDIT = "nochange"
	DOC_EDIT = "nochange"
	J_EDIT = ""
	BATCH_PATH = "C:/Users/p.bhagwat/AppData/Roaming/npm/node_modules/qunit-puppeteer/bin/BAE_4_4/"
    }
   
   stages {
   
   	   stage ('Print mode') {
          
				steps { 
					echo 'I only execute on the master branch.' 
					echo 'Result of previous build  ' + currentBuild.getPreviousBuild().result
					echo 'changed data       '+currentBuild.changeSets
					echo 'Env build number   ' +ENV_BUILD_NO
					echo 'BUILD_URL          ' +BUILD_URL
					echo 'BUILD_ID           ' +BUILD_ID 
					echo 'Jenkins URL        ' +JENKINS_URL
					echo 'JOB NAME   		 ' +JOB_NAME
					echo 'JOB BAE NAME   		 ' +JOB_BASE_NAME
					echo 'JENKINS HOME   	 ' +JENKINS_HOME
					echo 'JOB_URL  			 ' +JOB_URL
					echo 'GIT BRANCH   		 ' +GIT_BRANCH
					echo 'WORKSPACE   		 ' +WORKSPACE 
					
				bat  ''+ BATCH_PATH + 'sleep30.bat'

										
						}
										}
   
   
   	   
	   stage ('Build only on master') {
          
			 when { branch 'master' }
				steps { 
					echo 'I only execute on the master branch.' 
					echo 'Result of previous build  ' + currentBuild.getPreviousBuild().result
					echo 'changed data   '+currentBuild.changeSets
					echo 'Env build number   ' +ENV_BUILD_NO
					echo 'Jenkins URL   ' +JENKINS_URL
					echo 'JOB NAME   ' +JOB_NAME
					echo 'JENKINS HOME   ' +JENKINS_HOME
					echo 'GIT BRANCH   ' +GIT_BRANCH				
				

										
						}
										}
					
		stage ('Build only on non-master') {
				when { not { branch 'master' } }
					steps {
					echo 'I execute on non-master branches.'
					echo 'Result of previous build   ' + currentBuild.getPreviousBuild().result
					
					
					
					
					
		
					script{
			
					def changes = "Changes:\n"
					build = currentBuild
					while(build != null && build.result != 'SUCCESS') {
						changes += "In ${build.id}:\n"
						for (changeLog in build.changeSets) {
							for(entry in changeLog.items) {
								for(file in entry.affectedFiles) {
								
									changes += "* ${file.path}\n"
								}
							}
						}
						build = build.previousBuild
					}
					
					echo changes
					
					if (changes.indexOf("Documents") >= 0) {
						
						DOC_EDIT = "change"
		
							} 
					
					if (changes.indexOf("Code") >= 0) {
						
						CODE_EDIT = "change"
		
							} 
				
						echo CODE_EDIT
						echo DOC_EDIT
			}
				
				}
							}					
										
					
	
			stage ('Document zipping stage') {
			
          
			 when {   	  expression {
									return DOC_EDIT == 'change';
									}
					
			 }
			 
		
			 
			 
				steps { 
								
				echo 'Document zipping stage'
						}
								}
	
			
			stage ('Compile Stage Run') {
			
          
			 when {   	  expression {
									return CODE_EDIT == 'change';
									}		
			 }
			 
				steps { 
								
				echo 'Compile Stage Run'
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
