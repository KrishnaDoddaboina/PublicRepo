pipeline {
	agent any
	def SF_CONSUMER_KEY=env.CONNECTED_APP_CONSUMER_KEY_DH
    def SF_USERNAME=env.HUB_ORG_DH
    def SERVER_KEY_CREDENTALS_ID=env.JWT_CRED_ID_DH
    def TEST_LEVEL='RunLocalTests'
    def PACKAGE_NAME='0Ho1U000000CaUzSAK'
    def PACKAGE_VERSION
    def SF_INSTANCE_URL = env.SFDC_HOST_DH ?: "https://login.salesforce.com"
    def SFDC_USERNAME
    def toolbelt = tool 'toolbelt'
	stages {
		stage('checkout source') {
        checkout scm
		}
		stage('Authorize DevHub'){
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
