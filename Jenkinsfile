pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Kshitij247/mlops-iris-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh 'venv/bin/pip install --upgrade pip'
                sh 'venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Retrain Model') {
            steps {
                sh 'venv/bin/python retrain.py'
            }
        }

       stage('Deploy Model') {
            steps {
                sh 'cp iris_model.pkl /opt/mlops/iris_model.pkl'
            }
        }
    }
}
