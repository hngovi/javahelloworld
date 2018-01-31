pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
				sh 'mvn clean package'
            }
        }
    }
	post {
        always {
			archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
            junit 'build/reports/**/*.xml'
        }
    }
}