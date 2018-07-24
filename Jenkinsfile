pipeline {
    agent any

	
    environment {
	ENV_BUILD_NO = "${env.BUILD_NUMBER}"
	JENKINS_URL = "${env.JENKINS_URL}"
	JOB_NAME = "${env.JOB_NAME}"
	JENKINS_HOME = "${env.JENKINS_HOME}"
	GIT_BRANCH =    "${env.GIT_BRANCH}" 
	CODE_EDIT = ""
	DOC_EDIT = ""
	J_EDIT = ""
    }
   
   stages {
   
   
   	   stage ('calculate change') {
          
			steps{
			
			
			script{
			
			def getLastSuccessfulCommit() {
			  def lastSuccessfulHash = null
			  def lastSuccessfulBuild = currentBuild.rawBuild.getPreviousSuccessfulBuild()
			  if ( lastSuccessfulBuild ) {
				lastSuccessfulHash = commitHashForBuild( lastSuccessfulBuild )
			  }
			  return lastSuccessfulHash
			}
			
			
			def commitHashForBuild( build ) {
			  def scmAction = build?.actions.find { action -> action instanceof jenkins.scm.api.SCMRevisionAction }
			  return scmAction?.revision?.hash
}

			 def lastSuccessfulCommit = getLastSuccessfulCommit()
				  def currentCommit = commitHashForBuild( currentBuild.rawBuild )
				  if (lastSuccessfulCommit) {
					commits = sh(
					  script: "git rev-list $currentCommit \"^$lastSuccessfulCommit\"",
					  returnStdout: true
					).split('\n')
					println "Commits are: $commits"
				  }

			
			
			}
			
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
					def changeLogSets = currentBuild.changeSets
					for (int i = 0; i < changeLogSets.size(); i++) {
    					def entries = changeLogSets[i].items
  					  for (int j = 0; j < entries.length; j++) {
        				def entry = entries[j]
        				echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"
        				def files = new ArrayList(entry.affectedFiles)
        				for (int k = 0; k < files.size(); k++) {
            				def file = files[k]	
							
            				echo "editType name :  ${file.editType.name} "
							echo  "File path  : ${file.path}"
										
							if((${file.path}).includes("Documents"))
							{
							DOC_EDIT = "true"
							}
							
							if((${file.path}).includes("Code"))
							{
							CODE_EDIT = "true"
							}
							
							if((${file.path}).includes("Jenkinsfile"))
							{
							J_EDIT = "true"
							}
							
							
							echo "DOC_EDIT" + DOC_EDIT
							echo "CODE_EDIT" + CODE_EDIT
							echo "J EDIT" + J_EDIT
      							  }
   							 }
							}
						}
					echo 'changed data   '+currentBuild.changeSets
					echo 'Env build number   ' +ENV_BUILD_NO
					echo 'Jenkins URL   ' +JENKINS_URL
					echo 'JOB NAME  ' +JOB_NAME
					echo 'JENKINS HOME   ' +JENKINS_HOME
					echo 'GIT BRANCH   ' +GIT_BRANCH
				}
							}					
										
					
	
			stage ('Document zipping stage') {
          
			 when { branch 'master' }
				steps { 
								
				echo 'Document zipping stage'
						}
								}
	
			
			stage ('Compile Stage Run') {
          
			 when { branch 'master' }
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
