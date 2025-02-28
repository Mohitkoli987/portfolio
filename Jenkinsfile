pipeline {
    agent any

    environment {
        VENV = "venv"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Mohitkoli987/portfolio.git'
            }
        }

        stage('Setup Python Environment') {
            steps {
                sh 'python3 -m venv $VENV'
                sh 'source $VENV/bin/activate'
                sh 'pip install --upgrade pip'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'source $VENV/bin/activate && python -m unittest discover tests/'
            }
        }

        stage('Deploy') {
            steps {
                sh 'source $VENV/bin/activate && python app.py &'
            }
        }
    }
}
