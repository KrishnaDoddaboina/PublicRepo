#!groovy

import groovy.json.JsonSlurperClassic
import groovy.json.JsonSlurper
pipeline {
    agent any
    stages {
        stage('Example Username/Password') {
            environment {
               SFDX_USE_GENERIC_UNIX_KEYCHAIN = true
			   SF_CONSUMER_KEY = "3MVG9n_HvETGhr3C0IBETj._LtyhM_yb8HXMP2QSpyRVInHpJgdBkUXOJsfSwEASLwZxr2pqzmKpI_LWJz1jC"
			   SF_USERNAME = "krishna@rsystems.com.package"
			   SF_INSTANCE_URL = "https://login.salesforce.com"
			   SERVER_KEY_CREDENTALS_ID = "039c2d32-4253-4c49-8974-f652f3e0c125"
            }
            steps {
                echo "SF_CONSUMER_KEY =  ${env.SF_CONSUMER_KEY}"
				echo "SF_USERNAME =  ${env.SF_USERNAME}"
				echo "SF_INSTANCE_URL =  ${env.SF_INSTANCE_URL}"
				echo "SERVER_KEY_CREDENTALS_ID =  ${env.SERVER_KEY_CREDENTALS_ID}"
				
				echo "***************************************************************"
				
            }
        }
		stage (Authorization DevHub){
			environment {
               SFDX_USE_GENERIC_UNIX_KEYCHAIN = true
			   SF_CONSUMER_KEY = "3MVG9n_HvETGhr3C0IBETj._LtyhM_yb8HXMP2QSpyRVInHpJgdBkUXOJsfSwEASLwZxr2pqzmKpI_LWJz1jC"
			   SF_USERNAME = "krishna@rsystems.com.package"
			   SF_INSTANCE_URL = "https://login.salesforce.com"
			   SERVER_KEY_CREDENTALS_ID = "039c2d32-4253-4c49-8974-f652f3e0c125"
		
		}
		steps {
			println 'code in Authorize DevHub'
                    //rc = command "${toolbelt} force:auth:jwt:grant --instanceurl ${SF_INSTANCE_URL} --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --setalias HubOrg"
                    rc = command "${toolbelt} force:auth:jwt:grant --clientid ${SF_CONSUMER_TARGET_KEY} --username ${SF_USERNAME_TARGET} --jwtkeyfile \"${server_key_file}\" --setdefaultdevhubusername --instanceurl ${SF_INSTANCE_URL}   --setalias HubOrg"
                    println rc
                    if (rc != 0) {
                        println 'code in Authorize DevHub error block'
                        error 'Salesforce dev hub org authorization failed.'
                    }
		}
        
    }
}
