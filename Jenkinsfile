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
                //sh 'curl -X POST -H "Content-Type: application/json" -d "{\"chat_id\": \"881875692\", \"text\": \"Falló la tarea $JOB_NAME!!, ejecución $BUILD_NUMBER, \", \"disable_notification\": false}" https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "YEEEEEEAAA!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 2: Ejecutar script de python') {
            steps {
                echo 'Ejecutando script de python...'
                sh '/usr/bn/python3 python-diff-v2.py old.xlsx new.xlsx'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "YEEEEEEAAA!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 3: Script al servidor') {
            steps {
                echo 'Mandando el sh al servidor...'
                sh 'scp -i ~/puto.pem -p /home/ubuntu/workspace/A_la_primera/meta-script.sh  ubuntu@52.91.234.139:/home/ubuntu/meta-script.sh'
                //sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "YEEEEEEAAA!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 4: Ejecutar script de bash') {
            steps {
                echo 'Ejecutando script de bash...'
                //sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "YEEEEEEAAA!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 5: Creación de informe') {
            steps {
                echo 'Conformando PDF...'
                //sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "YEEEEEEAAA!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 6: Push a github') {
            steps {
                echo 'Haciendo un push a github...'
                //sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "YEEEEEEAAA!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 7: Notificando') {
            steps {
                echo 'Notificando...'
                //sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "YEEEEEEAAA!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
    }
}
