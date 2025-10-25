pipeline {
    agent any  // Можно заменить на agent { docker { image 'python:3.12-alpine' } }

    environment {
        APP_NAME = 'my_app'
        DOCKER_IMAGE = "myrepo/${APP_NAME}"
    }

    options {
        timestamps()        // Добавляет время к логам
        ansiColor('xterm')  // Цветной вывод
        skipStagesAfterUnstable()
    }

    stages {
        stage('Checkout') {
            steps {
                echo '📦 Получаем код из репозитория...'
                sh '''
                    ls -la
                
                '''
                checkout scm
            }
        }
    }

    post {
        success {
            echo "✅ Сборка завершена успешно!"
        }
        failure {
            echo "❌ Ошибка при сборке "
        }
    }
}
