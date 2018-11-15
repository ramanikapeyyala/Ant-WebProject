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
        bat 'cp $WORKSPACE/dist/*.war /Users/bhaskarreddyl/BhaskarReddyL/Softwares/Running/apache-tomcat-9.0.12/webapps/'
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
