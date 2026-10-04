pipeline {
    agent { label 'linux' }

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com'
            }
        }

        stage('Install System Python') {
            steps {
                // Uses yum to check and install python3 components if missing
                sh '''
                    echo "Checking and installing Python3 system packages..."
                    sudo yum update -y
                    sudo yum install -y python3
                '''
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'python3 -m venv .venv'
                sh '.venv/bin/python -m pip install --upgrade pip'
                sh '.venv/bin/python -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh '.venv/bin/python -m unittest discover -s tests'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Stopping old process on port ${PORT:-5000}..."
                    fuser -k "${PORT:-5000}/tcp" 2>/dev/null || true
                    
                    echo "Starting application..."
                    BUILD_ID=dontKillMe nohup .venv/bin/python app.py > app.log 2>&1 &
                '''
            }
        }
    }
}
