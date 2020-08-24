pipeline {
    agent any
    environment {
        // Removed other variables for clarity...
        SFDX_USE_GENERIC_UNIX_KEYCHAIN = true
        // ...
    }
    stages {    
        stage('TEST') {
            steps {
                withCredentials([file(credentialsId: 'SERVER_KEY_CREDENTALS_ID', variable: 'VAR_CERT_FILE')]) {
                    sh returnStdout: true, script: "${SFDX_HOME}/sfdx force:auth:jwt:grant --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${VAR_CERT_FILE} --setdefaultdevhubusername --instanceurl ${SF_INSTANCE_URL}"
                }
            }
        }
    }
}
