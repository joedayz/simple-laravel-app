pipeline {
    agent any
    
    environment {
        PHP_PATH = 'C:\\Tools\\php82\\php.exe' // Ruta a PHP en Windows
        COMPOSER_HOME = 'C:\\ProgramData\\ComposerSetup\\bin' // Ruta de Composer
        PATH = "${env.PATH};${PHP_PATH};${COMPOSER_HOME};${NODE_HOME}"
    }

    // stages {
    //     stage('Check Versions') {
    //         steps {
    //             bat 'php -v'
    //             bat 'composer -V'
    //             bat '"C:\\Program Files\\nodejs\\node.exe" -v'
    //             bat '"C:\\Program Files\\nodejs\\npm.cmd" -v'
    //         }
    //     }
    // }

     stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/joedayz/simple-laravel-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'composer install --no-interaction --prefer-dist'
            }
        }

        stage('Set Environment') {
            steps {
                bat 'copy .env.example .env'
                bat 'php artisan key:generate'
            }
        }

        stage('Run Migrations') {
            steps {
                bat 'php artisan migrate --force'
            }
        }

        stage('Build Assets') {
            steps {
                bat 'npm install'
                bat 'npm run build'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'php artisan test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment stage (adjust as needed)'
            }
        }
    }

}
