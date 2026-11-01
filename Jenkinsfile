pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub'
            }
        }

        stage('Check Java') {
            steps {
                bat 'java -version'
                bat 'mvn -version'
            }
        }

        stage('Compile Java') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Run Application') {
            steps {
                bat 'mvn exec:java -Dexec.mainClass=HelloJenkins'
            }
        }

    }

    post {
        success {
            echo 'Java build completed successfully!'
        }

        failure {
            echo 'Java build failed. Check Console Output.'
        }
    }
}
