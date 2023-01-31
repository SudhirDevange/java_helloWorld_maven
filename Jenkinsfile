pipeline {
    agent any

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                bat 'echo "Cleaned Up Workspace For Project."'
            }
        }

        stage('Code Checkout') {
            steps {
                bat 'echo "Code Checkout"'
               	checkout([
                $class: 'GitSCM', 
                branches: [[name: '*/main']], 
                userRemoteConfigs: [[url: 'https://github.com/SudhirDevange/java_helloWorld_maven.git']]
               ])
            }
        }

		stage("Read ReadMe.md file") {
			steps {
				bat 'type README.md'
			}
		}
    }   
}
