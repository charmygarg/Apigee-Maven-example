pipeline {
    agent any
    stages {
        stage('build') {
         when{
            branch 'develop'
          }
            steps {
            script {
                      withCredentials([
                        usernamePassword(credentialsId: 'apigee-credentials',
                          usernameVariable: 'username',
                          passwordVariable: 'password')
                      ]) {
                        print 'username=' + username + 'password=' + password
                 environment = "test"
                 sh "cd ./apigee/Billing && mvn clean install -P${environment} -Dusername=${username} -Dpassword=${password} -Doptions=override"
                      }
                    }
            }
        }
    }
}