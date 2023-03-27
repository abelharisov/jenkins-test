pipeline {
    agent {
        kubernetes {
          yaml '''
          spec:
            containers:
            - name: node
              image: node:16.14.2-alpine3.15
              command:
              - sleep
              args:
              - 99d
'''
        }
    }
    parameters {
        string(name: 'QASE_PROJECT_CODE', defaultValue: 'DEMO')
        string(name: 'QASE_RUN_ID', defaultValue: '')
        string(name: 'QASE_REPORT', defaultValue: '1')
        string(name: 'QASE_RUN_COMPLETE', defaultValue: '1')
        string(name: 'QASE_API_BASE_URL', defaultValue: 'https://api.qase.io/v1')
        credentials(name: 'QASE_API_TOKEN', credentialType: "Secret text")
    }
    environment { 
        QASE_API_TOKEN = credentials("${params.QASE_API_TOKEN}") 
    }
    stages {
        stage('Run tests') {
            steps {
                git url: 'https://github.com/abelharisov/jenkins-test.git', branch: 'main'
                container('node') {
                    sh 'env'
                    sh 'npm i'
                    sh 'npx jest'
                }
            }
        }
  }
}
