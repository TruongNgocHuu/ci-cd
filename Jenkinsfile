pipeline {
	agent any
		stages{
			stage('Upload to exchange') {
				steps {
					echo 'mvn -B -U -e -V clean -DskipTests deploy -s settings.xml'					
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