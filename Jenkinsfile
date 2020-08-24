pipeline {
    agent any
    environment {
        // Removed other variables for clarity...
        SFDX_USE_GENERIC_UNIX_KEYCHAIN = true
        SERVER_CREDENTALS = credentials('SERVER_KEY_CREDENTALS_ID')
        
        // ...
    }
    stages {    
        stage('Authorize DevHub') {
            steps {
                withCredentials([file(credentialsId: 'SERVER_KEY_CREDENTALS_ID', variable: 'server_key_file')]) {
                    sh returnStdout: true, script: "${toolbelt}/sfdx force:auth:jwt:grant --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --instanceurl ${SF_INSTANCE_URL}"
                }
            }
        }
    }
}
