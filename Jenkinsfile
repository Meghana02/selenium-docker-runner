pipeline {
    // master executor should be set to 0
    agent any
    stages {
		stage('Pull Latest Image') {
            steps {
                //sh
                bat "docker pull meghana2013/selenium-docker"
            }
        }
        stage('Start Grid') {
            steps {
                //sh
                bat "docker-compose up -d hub chrome firefox"
            }
        }
        stage('Run Test') {
            steps {
                //sh
                bat "docker-compose up  search-moduleChrome book-flight-moduleFF"
            }
        }
     }
	 post{
		always{
			archiveArtifacts artifacts:'output/**'
			bat "docker-compose down"
		}
		
	}
}