def gv
pipeline{
	agent any
	parameters{
		choice(name: 'VERSION',choices: ['1.1','1.2','1.3'], description:'')
	}
	stages{
		stage("build"){
			steps{
				echo 'building the application'
			}
		}
		stage("test"){
                        steps{
                                echo 'testing the application'
                        }
                }
		stage("deploy"){
			input{
				message "Select the environment to deploy to"
				ok "Done"
				parameters{
					choice(name: 'ENV',choices: ['dev','staging','prod'], description:'')
				}
			}
                        steps{
                                echo 'deploying the application'
				echo 'Deploy to ${ENV}"
                        }
                }

	}
}
