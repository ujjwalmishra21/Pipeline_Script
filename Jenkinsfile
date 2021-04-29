pipeline{
	agent none
	stages{
		stage('None-Parallel Stage'){
			agent{
				label "master"
			}
			steps{
				echo "This stage will be executed first"
			}
		}
		stage('Run Tests'){
			parallel{
				stage('Test on Windows'){
					agent{
						label "Windows_Node"
					}
					steps{
						echo "Task1 on Agent"
					}
				}
				stage('Test on Master'){
					agent{
						label "master"
					}
					steps{
						echo "Task1 on Master"
					}
				}
			}
		}
	}
	post{
		always{
			echo "This will run always"
		}
		success{
			echo "This will run only if successful"
		}
		failure{
			echo "This will run only if run was masked as unstable"
		}
		changed{
			echo "This will run only if the state of the Pipeline has changed"
			echo "For example, if the Pipeline was previously failing but is now successful"
		}
	}
}
