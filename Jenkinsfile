pipeline {
	agent {
		docker {
			image 'maven'
			args '-v $HOME/.m2/root/.m2'
		}
	}
	stages {
		stage (" Quality gate") {
			steps {
				script {
					withSonarQubeEnv('sonarserver') {
					sh 'mvn sonar:sonar' 
					}
					
		        stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true  
	      }
	    }
			}
				}
			}
		}
	}
}


		      
