pipeline {
   agent any
   environment {
      RELEASE='20.04'
   }

       parameters {
        choice(
                name: 'Person name',
                choices: ['Pepito', 'Juanito'],
                description: 'A name is a term used for identification by an external observer. They can identify a class or category of things,' + 
                            'or a single thing, either uniquely, or within a given context. The entity identified by a name is called its referent. ' +
                            'A personal name identifies, not necessarily uniquely, a specific individual human. The name of a specific entity is ' +
                            ' sometimes called a proper name (although that term has a philosophical meaning as well) and is, when consisting of only ' + 
                            'one word, a proper noun. Other nouns are sometimes called "common names" or (obsolete) "general names". A name can be' + 
                            ' given to a person, place, or thing; for example, parents can give their child a name or a scientist can give an element a name.'
        )

        choice(
                name: 'Tag_remote',
                choices: 'true\nfalse',
                description: '''Hosts where the Ansible playbook will run on. Choose \"all\" to deploy on every host for the specified inventory'''
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

               script {
                  if (params.Tag_remote.equals('true')){
                     env.TAG_REMOTE = 'true'
                  } else {
                     env.TAG_REMOTE = 'false'
                  }
               }
                              
            }
      }

      stage ('Tagging remote') {
         when {
            expression {
               return env.TAG_REMOTE.equals('true')
            }
         }
         
         steps {
            echo 'Tagging remote ...'

         }
      }

      stage('Pipeline ending') {
         steps {
            echo 'The pipeline is ending'
         }
      }


   }

}
