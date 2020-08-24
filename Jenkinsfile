pipeline {
	agent any
	environment {
        SF_CONSUMER_KEY= '3MVG9n_HvETGhr3C0IBETj._LtyhM_yb8HXMP2QSpyRVInHpJgdBkUXOJsfSwEASLwZxr2pqzmKpI_LWJz1jC'
		SF_USERNAME= 'krishna@rsystems.com.package'
		SF_INSTANCE_URL= 'https://login.salesforce.com'
		SERVER_KEY_CREDENTALS_ID= '039c2d32-4253-4c49-8974-f652f3e0c125'
	
    }
	stages {
		stage('checkout source') {
			steps {
				checkout scm
			}
		}
		stage('Authorize DevHub') {
			steps {
				withCredentials([file(credentialsId: SERVER_KEY_CREDENTALS_ID, variable: 'server_key_file')])) {
                    sh returnStdout: true, script: "${SFDX_HOME}/force:auth:jwt:grant --instanceurl ${SF_INSTANCE_URL} --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --setalias HubOrg"
                }
                    
			}
		}
	}
}
