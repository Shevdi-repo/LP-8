pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                sh 'docker run --rm -v $PWD:/app -w /app composer install'
            }
        }

        stage('Run unit tests') {
            steps {
                sh './vendor/bin/phpunit tests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t php-app .'
            }
        }

        stage('Deploy Locally') {
            steps {
                sh 'docker run -d -p 8088:80 php-app'
            }
        }
    }
}
