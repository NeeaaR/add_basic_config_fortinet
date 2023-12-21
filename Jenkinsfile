pipeline {
    agent any

    parameters {
        string(name: 'hostname', defaultValue: 'master', description: 'Hostname de l equipement')
        string(name: 'ip_address', defaultValue: '5.5.5.5', description: 'IP de l equipement')
        string(name: 'site', defaultValue: 'SIVM', description: 'Site de l equipement')
        string(name: 'rack', defaultValue: 'BXNEF2500', description: 'Rack de l equipement')
        string(name: 'position', defaultValue: '24', description: 'Position de l equipement')
        string(name: 'vpc', defaultValue: 'NO', description: 'VPC')

        activeChoice(choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'vpc', randomName: 'choice-parameter-3293278730731951', script: groovyScript(fallbackScript: [classpath: [], oldScript: '', sandbox: false, script: ''], script: [classpath: [], oldScript: '', sandbox: false, script: 'return["YES","NO"]'])) 
        activeChoiceHtml(choiceType: 'ET_FORMATTED_HTML', name: 'vpc_slave', omitValueField: true, randomName: 'choice-parameter-3293280698580322', referencedParameters: 'vpc', script: groovyScript(fallbackScript: [classpath: [], oldScript: '', sandbox: false, script: ''], script: [classpath: [], oldScript: '', sandbox: false, script: '''switch(vpc){

        case "YES":
        html=\'\'\'
        <label>VPC ID</label>
        <p></p>
        <input type="text" class="setting-input"  name="value" placeholder="VPC ID">
        <p>Rentrer le numéro du VPC</p>
        <label>Switch slave</label>
        <p></p>
        <input type="text" class="setting-input"  name="value" placeholder="Rentrer les informations du switch slave sous cette forme => HOSTNAME;IP_ADDRESS;SITE;RACK;POSITION">
        <p>Rentrer les informations du switch slave sous cette forme</p>
        \'\'\' 
        break

        case "NO":
        html= \'\'\'\'\'\'
        }

        return html''']))

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
