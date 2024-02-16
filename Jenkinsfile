pipeline {
    agent {
        node {
            label 'AWS_NODO'
        }
    }

    stages {
        stage('Paso 1: Clonar') {
            steps {
                echo 'Clonando repositorio...'
                sh 'curl -X POST -H "Content-Type: application/json" -d "{\"chat_id\": \"881875692\", \"text\": \"Falló la tarea $JOB_NAME!!, ejecución $BUILD_NUMBER, \", \"disable_notification\": true}" https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 2: Ejecutar script de python') {
            steps {
                echo 'Ejecutando script de python...'
                sh ''
            }
        }
        stage('Paso 3: Script al servidor') {
            steps {
                echo 'Mandando sh al servidor...'
            }
        }
        stage('Paso 4: Ejecutar script de bash') {
            steps {
                echo 'Ejecutando script de bash...'
            }
        }
        stage('Paso 5: Creación de informe') {
            steps {
                echo 'Conformando PDF...'
            }
        }
        stage('Paso 6: Push a github') {
            steps {
                echo 'Haciendo un push a github...'
            }
        }
        stage('Paso 7: Notificando') {
            steps {
                echo 'Notificando...'
            }
        }
    }
}
