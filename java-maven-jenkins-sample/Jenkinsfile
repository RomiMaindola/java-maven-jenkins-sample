pipeline {
    agent any

    tools {
        maven "Maven3"
        jdk "JDK25"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-credentials',
                    url: 'https://github.com/RomiMaindola/git/tree/975fef33878dbf941e4aea88f06f46ff16346b64/java-maven-jenkins-sample'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'target\\*.jar', fingerprint: true
                }
            }
        }
    }
}



