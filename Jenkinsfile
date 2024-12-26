pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Встановлення залежностей (у цьому випадку, встановлення Newman)
                    sh 'npm install -g newman'
                }
            }
        }

        stage('Run API Tests') {
            steps {
                script {
                    // Запуск API тестів Postman за допомогою Newman
                    sh 'newman run Cars.postman_collection -e Dev.postman_environment' 
                }
            }
        }
    }

    post {
        always {
            // Додаткові дії, які виконуються завжди, навіть якщо є помилки
            echo 'API test execution completed'
        }
    }
}
