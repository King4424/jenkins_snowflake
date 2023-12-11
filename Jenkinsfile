pipeline {
    agent {
        node {
            label '4fe829abeda3940e1d7a450bbce31af8faead0c7b51b97e3f1a62f3fbc0d7324' // Replace with your specific Docker label if needed
        }
    }

    stages {
        stage('Run schemachange') {
            steps {
                script {
                    sh "pip install schemachange --upgrade"
                    sh "schemachange -f migrations -a ${SF_ACCOUNT} -u ${SF_USERNAME} -r ${SF_ROLE} -w ${SF_WAREHOUSE} -d ${SF_DATABASE} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY --create-change-history-table"
                }
            }
        }
    }
}

