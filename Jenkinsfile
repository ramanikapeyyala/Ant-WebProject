try{
node{

  stage('Checkout') { 
      
      git credentialsId: '4862c36a-cb75-4ad6-a7dc-dad0abf563c8', url: 'https://github.com/devopstrainingblr/Ant-WebProject.git', branch: 'master'
    
  }
   
   
   stage('Build') {
     
         if (isUnix()) {
            bat "ant -f build-mt.xml" 
             /* bat "${mvnHome}/bin/mvn package" */
         
         } else {
            bat "ant -f build-mt.xml"
         }
      }
	  
 
 stage('Deploy')
   {
        bat 'echo "Starting to copy the build artifact"'
        bat 'copy C:\Users\LokeshReddy\.jenkins\workspace\pip-2-sample\dist*.war G:\DEVOPSSOFTWARES\apache-tomcat-9.0.10\webapps'
        bat'echo "Deployed  the build artifact into tomcat server successfully"'

      }


	stage('notification'){
	      mail  to: 'devopstrainingblr@gmail.com', cc: 'devopstrainingblr@gmail.com', bcc: 'devopstrainingblr@gmail.com',from: 'devopstrainingblr@gmail.com', replyTo: 'devopstrainingblr@gmail.com', subject: 'Build DOne' ,body: 'Buid Done '
  
    
	   }
 
}
}catch(error){
   echo 'Some error occured, Please verify' 
   throw error
}
