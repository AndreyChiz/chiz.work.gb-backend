pipeline {
    agent any
    // Или вариант:
    // agent { docker { image 'python:3.12-alpine' } }

    environment {
        APP_NAME = 'my_app'
        DOCKER_IMAGE = "myrepo/${APP_NAME}"
    }

    options {
        ansiColor('xterm')      // <── Цветной вывод в консоли
        timestamps()            // Время в логах
        skipStagesAfterUnstable()
    }

    stages {
        stage('Checkout') {
            steps {
                echo '\u001B[36m📦 Получаем код из репозитория...\u001B[0m'  // голубой
                sh '''
                    echo -e "\\033[33m==> Содержимое текущей директории:\\033[0m"
                    ls -la --color=always
                '''
                checkout scm
            }
        }
    }

    post {
        success {
            echo '\u001B[32m✅ Сборка завершена успешно!\u001B[0m'
        }
        failure {
            echo '\u001B[31m❌ Ошибка при сборке!\u001B[0m'
        }
    }
}
