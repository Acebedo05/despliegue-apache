pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {
        stage('Checkout') {
            steps {
                // Clonar el repositorio
		git 'https://github.com/Acebedo05/despliegue-apache.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Instalar dependencias de Node.js (npm)
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                // Compilar la aplicación React
                sh 'npm run build'
            }
        }

        stage('Deploy to Apache') {
            steps {
                // Copiar los archivos compilados a /var/www/html/
                sh 'sudo cp -r build/* ${DEPLOY_DIR}/'
            }
        }
    }

    post {
        success {
            echo "Despliegue exitoso."
        }
        failure {
            echo "El pipeline falló."
        }
    }
}
