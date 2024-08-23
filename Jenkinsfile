pipeline {
	agent any
		stages{
			stage('Upload to exchange') {
				steps {					
					bat 'mvn -B -U -e -V clean -DskipTests deploy -s settings.xml -X'
					echo 'Success'
				}
			}		
			stage('Build Clean package') {
				steps {
					bat 'mvn -B -U -e -V clean -DskipTests package -X'
					echo 'Success'
				}
			}
			stage('TEST') {
				steps {
					echo 'Go to step Test-App-With-Environment'
					bat 'mvn -Denv=dev test'
				}
			}
			stage('Deployment') {
				steps {
					bat 'mvn -B -U -e -V clean -DskipTests -Pdev deploy -DmuleDeploy'
				}
			}
		}
}