pipeline {
    agent any

    parameters {
        string(name: 'hostname', defaultValue: 'localhost', description: 'Nom d’hôte à utiliser')
    }

    stages {
        stage('Checkout') {
            steps {
                // Cloner le dépôt (ceci est implicite si vous utilisez une source de code intégrée à Jenkins)
                checkout scm

                sh 'sleep 30'
            }
        }

        stage('Fortinet') {
            steps {
                // Exécutez un script de test fictif. Adaptez ceci selon ce que vous avez dans votre dépôt.
                sh 'python3 test_script.py'
            }
        }

        stage('Build') {
            steps {
                // Exécutez un script de construction fictif. Adaptez ceci selon ce que vous avez dans votre dépôt.
                sh 'python3 build_script.py'
            }
        }
    }

    post {
        success {
            echo "Les étapes se sont terminées avec succès!"
        }
        failure {
            echo "Une étape a échoué."
        }
    }
}
