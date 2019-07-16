pipeline {
	agent any 
		stages {
			stage('One') {
				steps {
					echo 'Hi, this is Bego'
				}
			}
			stage('Two') {
				steps {
					input('Do you want to proceed')
				}
			}
			stage('Three') {
				when {
					not {
						branch "master"
					}
				}
				steps {
					echo "Hello"
				}
			}
			stage('Four') {
				parallel {
					stage('Unit Test') {
						steps {
							echo "Running the unit tests..."
						}
					}
					stage('Integration Test') {
						agent {
							docker {
								reuseNode true
								image 'ubuntu'
							}
						}
						steps {
							echo "Running the integration tests..."
						}
					}
				}
			}
		} 	
	
}