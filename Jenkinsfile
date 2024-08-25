pipeline {
	agent any
		environment {
			CREDENTIAL = credentials('creden')
		}
		stages{
			stage('Upload to exchange') {
				steps {					
					bat 'mvn -B -U -e -V clean -DskipTests -Dusername="%USER_NAME%" -Dpassword="%PASSWORD%" deploy -s settings.xml'
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
					echo 'Go to step Test-App-With-Environment'
					bat 'mvn -Denv=dev test -X'
				}
			}
			stage('Deployment') {
				steps {
					bat 'mvn -B -U -e -V clean -DskipTests -Pdev deploy -DmuleDeploy'
				}
			}
		}
}