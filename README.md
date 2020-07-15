# Infrastructure as code and automation:-  

	- Jenkins allow to use web UI to input all build parameters.
	- This leads to:
		- No easy history of changes
		- Segregation between Jenkins admins and developers
			- Users (often developers) will have to contact a Jenkins administrator to make changes.
			- Long lead time for changes
		- Difficult to backup and restore (e.g. how to restore just one setting to how it was the day before).

	- The solution is to completely write a job as code and save it in version control
		- Version control (git) gives you a history and audit trail.
		- Easy roll back to older versions of jobs and build instructions.
		- Allows operations to give more control to the developers.
			- Developers can bundle the jenkins build instructions with their own project repository. (e.g a. Jenkins File in their project directory)
			- This is what a company that wants to embrace DevOps should do: allow developers to control their own builds.

	- Two capabilities to enable Jenkins to be a true DevOps tool within your software organization:
		- Jenkins Job DSL
		- Jenkins Pipelines

	- Jenkins Job DSL:-
		-Write a code that creates and modifies jenkins jobs automatically

	- Jenkins Pipeline (Jenkins File):-
		- Bundle the build parameters within the project
		- Allow developers to change jenkins build parameters
		- Enable audit trial, history, rollbacks using version control 

******************************************************************************************************************************************************************

Jenkins DSL:-
-------------
	- Jenkins Job DSL plugin was designed to make it easier to manage jobs.

		- If you don't have a lot of jobs,  using the UI is the easiest way.
		- When the jobs grow, maintaining becomes difficult and lot of work.

	- Jenking Job DSL benefits:-

		- Version control, history, audit log, easier job restore when something goes wrong.
********************************************************************************************************************************************************************


Pre-request:- install job DSL plug-in


Step01: Create new Freestyle job as "Seed_Job".
Step02: within seed job, under Build tab choose "Use provided DSL script"
Step03: Write DSL Script,
			
			step1: create a job
					
					job("jobName"){

					}

			step2: run ur current build

			step3: add description in ur existing DSL Script

					 job("jobName"){

					 	description('Test Automation for LeafTaps')

					}

			step4: run ur current build

			step5: add source code management in ur existing DSL Script

					job("jobName"){

					 	description('Test Automation for LeafTaps')

					 	scm{
					 		 git('https://github.com/GopinathJayakumar/ACMEBuild', 'master')
					 	}


					}

			step6: run ur current build

			step7: add build trigger configuration

					job("jobName"){

					 	description('Test Automation for LeafTaps')

					 	scm{
					 		 git('https://github.com/GopinathJayakumar/ACMEBuild', 'master')
					 	}

					 	triggers {
        					scm('* * * * *')
    					}
					}

			step8: run ur current build

			step9: add the steps - build execution setup

					job("jobName"){

						  description('Test Automation for LeafTaps')
						  
						  scm{
						    git('https://github.com/GopinathJayakumar/ACMEBuild', 'master')
							}
						  
						  triggers {
						        scm('* * * * *')
						    }

						  steps{
						    maven('package')
						  }
					}

				step10: run ur current build





