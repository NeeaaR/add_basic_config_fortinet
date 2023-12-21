properties ([
    parameters([
        string(name: 'hostname', defaultValue: 'master', description: 'Hostname de l equipement'),
        string(name: 'ip_address', defaultValue: '5.5.5.5', description: 'IP de l equipement'),
        string(name: 'site', defaultValue: 'SIVM', description: 'Site de l equipement'),
        string(name: 'rack', defaultValue: 'BXNEF2500', description: 'Rack de l equipement'),
        string(name: 'position', defaultValue: '24', description: 'Position de l equipement'),
        string(name: 'vpc', defaultValue: 'NO', description: 'VPC'),

        activeChoice(choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'vpc', randomName: 'choice-parameter-3291913559104882', script: groovyScript(fallbackScript: [classpath: [], oldScript: '', sandbox: false, script: 'return["error"]'], script: [classpath: [], oldScript: '', sandbox: false, script: 'return["YES","NO"]'])), activeChoiceHtml(choiceType: 'ET_FORMATTED_HTML', name: 'vpc_slave', omitValueField: false, randomName: 'choice-parameter-3291913565760138', referencedParameters: 'vpc', script: groovyScript(fallbackScript: [classpath: [], oldScript: '', sandbox: false, script: 'return["error"]'], script: [classpath: [], oldScript: '', sandbox: false, script: '''switch(vpc){

        case "YES":
        html=\'\'\'
        <label>VPC ID</label>
        <p></p>
        <input type="text" class="setting-input"  name="value" placeholder="VPC ID">
        <p>Rentrer le numéro du VPC</p>
        <label>Switch slave</label>
        <p></p>
        <input type="text" class="setting-input"  name="value" placeholder="Rentrer les informations du switch slave sous cette forme => HOSTNAME;IP_ADDRESS;SITE;RACK;POSITION">
        <p>Rentrer les informations du switch slave sous cette forme => n9ktest1;10.222.240.60;SIVM;BXNEF2500;24</p>
        \'\'\' 
        break

        case "NO":
        html= \'\'\'\'\'\'
        }

        return html''']))
    ])
])

ansiColor('xterm') {
    node('maître') {
        WORKSPACE = "${WORKSPACE}/{BUILD_TAG}"
        ws("${WORKSPACE}") {

            stage('Preparation') {
                sh 'echo "Preparation"'
                sh 'echo "Hostname : ${hostname}"'
                sh 'echo "IP : ${ip_address}"'
                sh 'echo "Site : ${site}"'
                sh 'echo "Rack : ${rack}"'
                sh 'echo "Position : ${position}"'
                sh 'echo "VPC : ${vpc}"'
                sh 'echo "VPC slave : ${vpc_slave}"'
            }

            stage('Cleanup') {
                try {
                    cleanWS notFailBuild: true
                } catch (err) {
                    echo "Error cleaning workspace: ${err}"
                    currentBuild.result = 'FAILURE'
                }
            }

        }
    }
}