pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'export MAVEN_HOME=/var/jenkins_home/apache-maven-3.6.3'
                sh '$MAVEN_HOME/bin/mvn --version'
				sh '$MAVEN_HOME/bin/mvn clean package'
            }
        }
    }
	post {
        always {
			archiveArtifacts artifacts: '**/*.jar', fingerprint: true
        }
    }
}