pipeline {
	agent any
	stages {
		stage("build") {
			when {
				branch 'develop'
			}
			steps {
				echo 'build'
				sh '''
					docker-compose build
				'''
			}
		}
		stage("test") {
			when {
				branch 'develop'
			}
			steps {
				echo 'test'
				sh '''
					docker-compose up --force-recreate --exit-code-from SumaTest SumaTest
				'''
			}
		}
		stage("deploy") {
			when {
				branch 'develop'
			}
			steps {
				echo 'deploy'
				sh '''
					docker-compose up -d --force-recreate Suma
					docker-compose up -d --force-recreate SitioWeb
				'''
			}
		}
	}
}