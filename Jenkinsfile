podTemplate(containers: [
    containerTemplate(name: 'node', image: 'node:16.14.2-alpine3.15', command: 'sleep', args: '99d')
  ]) {

    node(POD_LABEL) {
        parameters {
            string(name: 'QASE_PROJECT_CODE')
            string(name: 'QASE_RUN_ID')
            string(name: 'QASE_REPORT')
            string(name: 'QASE_RUN_COMPLETE')
            string(name: 'QASE_API_BASE_URL')
        }
        
        stage('Test') {
            container('node') {
                stage('Shell Execution') {
                    sh '''
                    git clone https://github.com/abelharisov/jenkins-test.git
                    cd jenkins-test
                    npm i
                    npx jest
                    '''
                }
            }
        }

    }
}
