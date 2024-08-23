pipeline {
	agent any
		stages{
			stage('Upload to exchange') {
				steps {
					bat 'mvn -B -U -e -V clean -DskipTests deploy -X'
					echo 'Success'
				}
			}		
			stage('Build Clean package') {
				steps {
					bat 'mvn -B -U -e -V clean -DskipTests package'
					echo 'Success'
				}
			}
			stage('TEST') {
				steps {
					bat 'mvn test'
				}
			}
			stage('Deployment') {
				steps {
					bat 'mvn -B -U -e -V clean -DskipTests -Pdev deploy -DmuleDeploy'
				}
			}
		}
}