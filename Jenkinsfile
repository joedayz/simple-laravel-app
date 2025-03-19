pipeline {
    agent any
    
    environment {
        PHP_PATH = 'C:\\Tools\\php82\\php.exe' // Ruta a PHP en Windows
        COMPOSER_HOME = 'C:\\ProgramData\\ComposerSetup\\bin' // Ruta de Composer
        PATH = "${env.PATH};${PHP_PATH};${COMPOSER_HOME};${NODE_HOME}"
    }

    stages {
        stage('Check Versions') {
            steps {
                bat 'php -v'
                bat 'composer -V'
                bat '"C:\\Program Files\\nodejs\\node.exe" -v'
                bat '"C:\\Program Files\\nodejs\\npm.cmd" -v'
            }
        }
    }
}
