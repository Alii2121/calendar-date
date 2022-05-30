pipeline {
 agent any

 stages {
     stage('verify branch'){
         steps {
        echo '$GIT_BRANCH'

         }

     }

     stage('Build docker image'){
     steps{
         
         bat(script: '''
         docker image build -t alimarawan2121/cal-date:cal .
         ''')

     }
     }
     stage('Push to dockerhub'){
     steps{
      echo "Workspace is $WORKSPACE"
              dir("$WORKSPACE") {
              script {
                  docker.withRegistry('https://index.docker.io/v1/', 'dockerhub4') {
                      def image = docker.build('alimarawan2121/cal-date:latest')
                      image.push()
                  }
              }

     }


     }

 }

}
}