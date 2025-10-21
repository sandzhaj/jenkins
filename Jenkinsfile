pipeline {
    agent any

    environment {
        APP_NAME = 'my_app'
        ALEX_CRED = credentials('alexcreds')
        SECTET_NEW = credentials('secrettext')
    }

    stages {
        stage('Переменные окружения') {
            steps {
                sh"""
                set +x
                echo "Имя приложения (APP_NAME) = $env.APP_NAME"
                echo $SECTET_NEW
                """
            
            }
        }
    }
}
