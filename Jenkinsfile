pipeline{
	agent any
	stages{
	stage("Pull Latest Image"){
			steps{
				bat "docker pull dianew/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				bat "docker-compose up --no-color -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up --no-color search-module book-flight-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			bat "docker-compose down"
		}
	}
}