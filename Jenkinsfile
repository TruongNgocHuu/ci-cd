pipeline {
	agent any
		stages{
			stage('Build') {
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