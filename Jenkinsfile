pipeline {
    agent {
        node {
            label 'AWS_NODO'
        }
    }
    //environment {
    //    git = credentials('token')
    //}
    stages {
        stage('Paso 1: Clonar') {
            steps {
                echo 'Clonando repositorio...'
                //sh 'curl -X POST -H "Content-Type: application/json" -d "{\"chat_id\": \"881875692\", \"text\": \"Falló la tarea $JOB_NAME!!, ejecución $BUILD_NUMBER, \", \"disable_notification\": false}" https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "Repo!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
                // Enviar documento (Funciona)
                // sh 'curl -X  POST "https://api.telegram.org/bot"6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ"/sendDocument" -F chat_id="881875692" -F document="@new.xlsx"'
            }
        }
        stage('Paso 2: Ejecutar script de python') {
            steps {
                echo 'Ejecutando script de python...'
                sh '/usr/bin/python3 python-diff-v2.py old.xlsx new.xlsx'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "Script!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 3: Script al servidor') {
            steps {
                echo 'Mandando el sh al servidor...'
                // Cambiar el script chorra por el meta-script
                sh 'scp -i ~/puto.pem -p /home/ubuntu/workspace/A_la_primera/meta-script.sh  ubuntu@servjenkins.duckdns.org:/home/ubuntu/meta-script.sh'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "Mandado!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 4: Ejecutar script de bash') {
            steps {
                echo 'Ejecutando script de bash...'
                // ssh para ejecutar
                sh 'ssh -i ~/puto.pem ubuntu@servjenkins.duckdns.org "touch hola"'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "Ejecutado!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 5: Creación de informe') {
            steps {
                echo 'Conformando PDF...'
                sh '/usr/bin/python3 md2pdf.py info.md info.pdf'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "PDF!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
        stage('Paso 6: Enviando PDF') {
            steps {
                echo 'Enviando...'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "Enviado!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
                sh 'curl -X  POST "https://api.telegram.org/bot"6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ"/sendDocument" -F chat_id="881875692" -F document="@info.pdf"'
            }
        }
        stage('Paso 7: Push a github') {
            steps {
                echo 'Haciendo un push a github...'
                
            }
        }
        stage('Paso 8: Notificando') {
            steps {
                echo 'Notificando...'
                sh 'curl -X POST -H \'Content-Type: application/json\' -d \'{"chat_id": "881875692", "text": "Terminado!!!", "disable_notification": false}\'  https://api.telegram.org/bot6791917046:AAHuW0hZOl5D5raRyx1R11MWY7fIYHi66xQ/sendMessage'
            }
        }
    }
post {
    success {
        script {
            // Imprimir variables de entorno
            echo "Variable de entorno proporcionada por Jenkins:"
            echo "JOB_NAME: ${env.JOB_NAME}"
            echo "BUILD_NUMBER: ${env.BUILD_NUMBER}"
            echo "BUILD_ID: ${env.BUILD_ID}"
            echo "BUILD_URL: ${env.BUILD_URL}"
            echo "JOB_URL: ${env.JOB_URL}"
        }
    }
    failure {
        //Lo intenté pero no salió
        sh "cat ${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_NUMBER}/log >> log.txt"
    }
}


}
