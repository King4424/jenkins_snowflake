pipeline {
    agent any

    stages {
        stage('Run schemachange') {
            steps {
                script {
                    sh "docker run --rm -u 0:0 -v $PWD:/workspace -w /workspace python:3.8 pip install schemachange --upgrade"
                    sh "docker run --rm -u 0:0 -v $PWD:/workspace -w /workspace python:3.8 schemachange -f migrations -a ${SF_ACCOUNT} -u ${SF_USERNAME} -r ${SF_ROLE} -w ${SF_WAREHOUSE} -d ${SF_DATABASE} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY --create-change-history-table"
                }
            }
        }
    }
}

