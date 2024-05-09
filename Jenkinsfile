pipeline{
	agent any
	tools{
		maven 'maven-3.9'
	}
	stages{
		stage("build jar"){
			steps{
				echo "building the application.."
				sh 'mvn package'
			}
		}
		stage("build image"){
			steps{
				echo "building the docker image"
				withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]){
					sh 'docker build -t chintu413/demo-app:jma-2.0 .'
					sh 'echo $PASS docker login -u $USER --password-stdin'
					sh 'docker push chintu413/demo-app:jma-2.0'
				}
			}
		}
		stage("build jar"){
			steps{
				echo "building the application.."
				sh 'mvn package'
			}
		}
		
	}
}
