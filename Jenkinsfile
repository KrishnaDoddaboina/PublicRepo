pipeline {
    agent any
    environment {
        // Removed other variables for clarity...
       def SFDX_USE_GENERIC_UNIX_KEYCHAIN = true
       def SF_CONSUMER_KEY = "3MVG9n_HvETGhr3C0IBETj._LtyhM_yb8HXMP2QSpyRVInHpJgdBkUXOJsfSwEASLwZxr2pqzmKpI_LWJz1jC"
       def SF_USERNAME = "krishna@rsystems.com.package"
       def  SF_INSTANCE_URL = "https://login.salesforce.com"
       def  SERVER_KEY_CREDENTALS_ID = "039c2d32-4253-4c49-8974-f652f3e0c125"
        
        
        // ...
    }
    stages {    
        stage('Authorize DevHub') {
            steps {
                withCredentials([file(credentialsId: 'server.key', variable: 'server_key_file')]) {
                    sh returnStdout: true, script: "${toolbelt}/sfdx force:auth:jwt:grant --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --instanceurl ${SF_INSTANCE_URL}"
                }
            }
        }
    }
}
