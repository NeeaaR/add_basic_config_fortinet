properties([
  parameters([

    string(name: 'environment', defaultValue: 'DEV', description: 'Environment'),
    string(name: 'hostname', defaultValue: 'test', description: 'Hostname'),
    string(name: 'ip_address', defaultValue: 'NO', description: 'Adresse IP'),

    activeChoice(choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'vpc', randomName: 'choice-parameter-3293988836860112', script: groovyScript(fallbackScript: [classpath: [], oldScript: '', sandbox: false, script: 'return ["error"]'], script: [classpath: [], oldScript: '', sandbox: false, script: 'return ["YES","NO"]'])), activeChoiceHtml(choiceType: 'ET_FORMATTED_HTML', name: 'vpc_slave', omitValueField: true, randomName: 'choice-parameter-3293988842741444', referencedParameters: 'vpc', script: groovyScript(fallbackScript: [classpath: [], oldScript: '', sandbox: false, script: 'return ["error"]'], script: [classpath: [], oldScript: '', sandbox: false, script: '''switch(vpc){

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

pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo "${params.Environment}"
        echo "${params.Host}"
      }
    }
  }
}