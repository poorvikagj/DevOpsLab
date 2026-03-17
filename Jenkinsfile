pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/poorvikagj/DevOpsLab.git'
            }
        }

        stage('Validate Files') {
            steps {
                sh '''
                    if ls *.txt 1> /dev/null 2>&1; then
                        echo "Text files found!"
                    else
                        echo "No text files found!" && exit 1
                    fi
                '''
            }
        }
    }
}