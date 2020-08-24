pipeline {
    agent any
    environment {
        // Removed other variables for clarity...
        SFDX_USE_GENERIC_UNIX_KEYCHAIN = true
        SERVER_CREDENTALS = credentials('039c2d32-4253-4c49-8974-f652f3e0c125')
        
        // ...
    }
    stages {    
        stage('Authorize DevHub') {
            steps {
                withCredentials([file(credentialsId: 'env.SERVER_CREDENTALS', variable: 'server_key_file')]) {
                    sh returnStdout: true, script: "${toolbelt}/sfdx force:auth:jwt:grant --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --instanceurl ${SF_INSTANCE_URL}"
                }
            }
        }
    }
}
