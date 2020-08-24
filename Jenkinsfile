#!groovy

import groovy.json.JsonSlurperClassic
import groovy.json.JsonSlurper

pipeline {
	agent any
	environment {
         SF_CONSUMER_KEY= 'CONNECTED_APP_CONSUMER_KEY_DH'
		 SF_USERNAME= 'HUB_ORG_DH'
		 SF_USERNAME_TARGET= 'HUB_TARGET_ORG_DH'
		 SERVER_KEY_CREDENTALS_ID= 'JWT_CRED_ID_DH'
	
    }
	stages {
		stage('checkout source') {
			steps {
				checkout scm
			}
		}
		stage('Authorize DevHub') {
			steps {
				println 'code in Authorize DevHub'
				rc = command "${toolbelt} force:auth:jwt:grant --instanceurl ${SF_INSTANCE_URL} --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --setalias HubOrg"
                    println rc
                    if (rc != 0) {
                        println 'code in Authorize DevHub error block'
                        error 'Salesforce dev hub org authorization failed.'
                    }
			}
		}
	}
}
