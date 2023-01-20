pipeline {
  agent {
        label 'master'
    }
  stages { 
    stage('Build') {
        agent {
        label 'master'
        }
        steps {
          sh "docker build -t apachetomcat:latest ."
          echo 'Docker image is created successfully'
        }
    }
   
    stage('publish-image') {
        agent {
        label 'master'
        }
        steps {
          sh "docker login -u ravali1505 -p ravali@123"
          sh "docker tag apachetomcat:latest ravali1505/pipeline"
          sh "docker push ravali1505/pipeline "
          echo 'The image is successfully pushed'
        }
      }
   }
 post {  
   always {  
     echo 'This will always run'  
   }  
   success {  
     echo 'This will run only if successful'  
   }  
   failure {  
     mail bcc: '', body: "<b>Example</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: 'ravali.ganigapeta@testingxperts.com', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "campus.venky@gmail.com";  
   }  
   unstable {  
     echo 'This will run only if the run was marked as unstable'  
   }  
   changed {  
     echo 'This will run only if the state of the Pipeline has changed'  
   }  
 }
}
