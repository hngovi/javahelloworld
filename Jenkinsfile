pipeline {
    agent any
    stages {
        stage('Sonarqube analysis') {
            steps {
               echo 'Running analysis...'
               withSonarQubeEnv('sonarqube') {
                   sh "mvn sonar:sonar"
               }
            }
        }

        stage('Quality gate') {
            steps {
               echo 'Waiting for quality gate...'
               waitForQualityGate abortPipeline: true
            }
        }

        stage('build') {
            steps {
                echo 'Build...'
                sh 'mvn --version'
				sh 'mvn clean package'
            }
        }
    }
	post {
        always {
			archiveArtifacts artifacts: '**/*.jar', fingerprint: true
        }
    }
}