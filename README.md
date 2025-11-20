# nagios-ngrok
ngrok-35hXpswZ3NeuIarHPGvKiTPffFn_3q3HdBy8FksmhYWZcB1Fd
script--pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
    }

    stages {

        stage('Git Repo & Clean') {
            steps {
                bat "git clone https://github.com/Sreenidhi09/jenkins_web.git"

                // go into folder after cloning
                bat "cd jenkins_web && mvn clean"
            }
        }

        stage('Install') {
            steps {
                bat "cd jenkins_web && mvn install"
            }
        }

        stage('Test') {
            steps {
                bat "cd jenkins_web && mvn test"
            }
        }

        stage('Package') {
            steps {
                bat 'cd jenkins_web && mvn package'
            }
        }
    }
}
