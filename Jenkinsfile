pipeline {
   agent any
   environment {
      RELEASE='20.04'
   }

       parameters {
        choice(
                name: 'INVENTORY',
                choices: ['inventories/staging/ubim2-validation/hosts.yml', "inventories/staging/fuc-debian11/hosts.yml", "inventories/production/tub-debian11/hosts.yml",'inventories/production/fub-debian11/hosts.yml'],
                description: 'Target inventory'
        )

        choice(
                name: 'TARGET_HOSTS',
                choices: 'Choose host for the proper inventory\n------\nall\n------\nhqit-valubim11-01\nhqit-valubim11-02\nhqit-valubim11-03\nhqit-valubim11-04\n------\nfuc-ubim11-01\nfuc-ubim11-02\nfuc-ubim11-03\nfuc-ubim11-04\n------\nfub-ubim11-01\nfub-ubim11-02\nfub-ubim11-03\nfub-ubim11-04\n------\ntub-ubim11-01\ntub-ubim11-02\ntub-ubim11-03\ntub-ubim11-04',
                description: '''Hosts where the Ansible playbook will run on. Choose \"all\" to deploy on every host for the specified inventory
            '''
        )


    }


   stages {
      stage('Build5') {
            environment {
               LOG_LEVEL='INFO'
            }
            steps {
               echo "Building release ${RELEASE} with log level ${LOG_LEVEL}..."
            }
        }
      stage('Test') {
            environment {
               FILE_CONTENT = "This is the content I want to write in the file.\n" +
                                "It is a very important content as you can see."
            }
            steps {
               echo "Testing release ${RELEASE}"
                              
            }
        }
   }

}
