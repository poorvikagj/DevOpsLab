pipeline {
    agent any

    tools {
        maven 'Maven3'      // Make sure Maven is configured in Jenkins
        jdk 'JDK25'         // Optional if you don't really need Java
    }

    environment {
        PROJECT_NAME = "TextProject"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Cloning repository..."
                git branch: 'main', url: 'https://github.com/poorvikagj/DevOpsLab.git'
            }
        }

        stage('Validate Files') {
            steps {
                echo "Checking .txt files..."
                sh '''
                    if ls *.txt 1> /dev/null 2>&1; then
                        echo "Text files found!"
                    else
                        echo "No text files found!" && exit 1
                    fi
                '''
            }
        }

        stage('Build (Maven)') {
            steps {
                echo "Running Maven build (even if minimal)..."
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test (Dummy)') {
            steps {
                echo "Running dummy test..."
                sh '''
                    echo "Simulating tests..."
                    sleep 2
                    echo "Tests passed!"
                '''
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo "Archiving .txt files..."
                archiveArtifacts artifacts: '*.txt', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
        always {
            echo "Pipeline finished."
        }
    }
}