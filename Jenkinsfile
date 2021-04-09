pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'export MAVEN_HOME=/var/jenkins_home/apache-maven-3.6.3'
                sh 'export PATH=$PATH:$MAVEN_HOME/bin'
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