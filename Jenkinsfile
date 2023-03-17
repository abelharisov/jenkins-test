podTemplate(containers: [
    containerTemplate(
        name: 'node',
        image: 'node:16.17.1-alpine'
        )
  ]) {

    node(POD_LABEL) {
        stage('Run tests') {
            container('node') {
                stage('Shell Execution') {
                    sh '''
                    'npm i'
                    'npx jest'
                    '''
                }
            }
        }
    }
}
