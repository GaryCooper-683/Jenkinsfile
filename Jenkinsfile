pipeline {
     agent any
     stage {
       stage ("Build") {
           steps {
               sh 'echo "Hello World"'
               sh '''
                   echo "Multiline shell step work too"
                   ls -lah
               '''
             }
         }
     }
}
