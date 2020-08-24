pipeline {
	agent any
	stages {
		stage('checkout source') {
			steps {
				checkout scm
			}
		}
		stage('Authorize DevHub') {
			steps {
				println 'code in Authorize DevHub'
				rc = command "${toolbelt} force:auth:jwt:grant --clientid ${SF_CONSUMER_TARGET_KEY} --username ${SF_USERNAME_TARGET} --jwtkeyfile \"${server_key_file}\" --setdefaultdevhubusername --instanceurl ${SF_INSTANCE_URL}   --setalias HubOrg"
                    println rc
                    if (rc != 0) {
                        println 'code in Authorize DevHub error block'
                        error 'Salesforce dev hub org authorization failed.'
                    }
			}
		}
	}
}
