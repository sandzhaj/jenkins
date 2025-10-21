pipeline {
    agent any

    environment {
        APP_NAME = 'my_app'
        ALEX_CRED = credentials('alexcreds')
        SECTET_NEW = credentials('secrettext')
    }

    options {
        timeout(time: 10, unit: 'MINUTES')
        buildDiscarder(logRotator(numToKeepStr: '5'))
        timestamps()
        disableConcurrentBuilds()
    }

    parameters {
        string(name: 'GIT_URL', defaultValue: '', description: '')
        booleanParam(name: 'BOOL', defaultValue: true, description: '')
        choice(name: 'ENV', choices: ["dev", "test", "prod"], description: '')
    }

    stages {
        stage('Переменные окружения') {
            steps {
                sh"""
                set +x
                echo "Имя приложения (APP_NAME) = $env.APP_NAME"
                echo SECTET_NEW = $SECTET_NEW
                echo "ALEX_CRED_USR = $ALEX_CRED_USR"
                echo "ALEX_CRED_PSW = $ALEX_CRED_PSW"
                """
            }
        }
        stage('Параметры') {
            steps {
                sh"""
                set +x
                echo "GIT_URL = $env.GIT_URL"
                echo BOOL = $BOOL
                echo "ENV = $ENV"
                """
            }
        }
    }
    post {
        always {
            sh "echo Завершаем билд"
        }
        success {
            sh "echo Все ок"
        }
        failure {
            sh "echo Все не ок"
        }
    
    }
}
