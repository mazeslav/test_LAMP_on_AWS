node {
    def err = false
    ws("/var/jenkins_home/workspace/${env.JOB_NAME}-${env.BUILD_NUMBER}") {
        try {
            
	
			/*tools {
					maven '3.5.2'
					jdk 'jdk8'
				  }*/

	

            stage('Checkout') {
                sh"echo `Checking out code"
                def scmVars = checkout([
                    $class: GitSCM, branches: scm.branches,
                    doGenerateSubmoduleConfigurations: scm.doGenerateSubmoduleConfigurations,
                    extensions: [
                        [$class: 'RelativeTargetDirectory', relativeTargetDir: 'build'],
                        [$class: 'WipeWorkspace']
                    ],
                    submoduleCfg: [],
                    userRemoteConfigs: scm.userRemoteConfigs
                ])
		
					/*def url = sh(returnStdout: true, script: 'git config remote.origin.url').trim()*/

					
					sh("echo ${scmVars.GIT_COMMIT} > git_commit.txt")
					sh("echo ${scmVars.GIT_BRANCH} > git_branch.txt")
					
					def GIT_COMMIT = readFile("git_commit.txt").trim()
					def GIT_BRANCH = readFile("git_branch.txt").trim()
				
					echo “Logging in Docker user”
          			
			}


					if (GIT_URL.contains("[microservice]")) {
	
						stage('Manual Release'){
							
											
							
							while (1) {
							def userInput =  timeout(time:60, unit:'SECONDS') 
											 {
												 input(id: 'userInput', message: 'Type command. \'exit\' for cancel', parameters: [[$class: 'TextParameterDefinition', defaultValue: '', description: '', name: ''],])
							  				 } 

								if (userInput=='exit') 
								  break
								sh "$userInput"

							}
					
						}
					 }

					else {

						 stage('Compile') {								

								echo "Compile"
								sh"mvn"
								if(GIT_BRANCH == "development") {

									sh "echo dev"
									
								}
							}													
					  }	 

	}

catch (e) {
            echo ‘Error: ’ + e.toString()
         	currentBuild.result = “FAILURE”

        }
        finally {
            
           "echo The End"

            
		}
    
	}
}
