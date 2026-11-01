pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching Java code from GitHub'
            }
        }

        stage('Check Java and Maven') {
            steps {
                bat 'java -version'
                bat 'mvn -version'
            }
        }

        stage('Compile') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Run Java Application') {
            steps {
                bat 'mvn exec:java -Dexec.mainClass=HelloJenkins'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Java application executed!'
        }

        failure {
            echo 'FAILURE: Check the build console output.'
        }
    }
}
