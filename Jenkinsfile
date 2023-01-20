pipeline {
  agent {
        label 'master'
    }
  stages { 
      //stage('clone') {
        //steps {
         // git branch: 'main', credentialsId: 'github-tocken', url: 'https://github.com/ganigapetaravali/multibranch.git'
          //echo 'Clone is susscessful from github'
       // }
     // }
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
}
// stage('Email-Notification') {
  //  agent {
    //  label 'master'
    //}
    //steps {
      //emailext mimeType: 'text/html',               
      //subject: "[Jenkins]${currentBuild.fullDisplayName}",               
      //to: "ravali.ganigapeta@testingxperts.com",             
      //body: """Please go to console output of ${BUILD_URL}input to approve or Reject"""  
      //input(id: 'Proceed1', message: 'Promote build?', parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']])
      //sh "docker build -t apachetomcat:latest ."
        //  }
       //}
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
             echo 'For example, if the Pipeline was previously failing but is now successful'  
         }  
     }  
 }

