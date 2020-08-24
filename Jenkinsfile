#!groovy

import groovy.json.JsonSlurperClassic
import groovy.json.JsonSlurper

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
