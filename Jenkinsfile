pipeline 
{   
   agent {
     label 'Build-Nginix'
         } 
     parameters 
           choice(choices: 'dev\nsyst\nmaster', description: 'Enter Branch Name ' , name: 'Branch_Name')    
     stages 
    {
       stage ('Checkout') 
          {
           steps {
             node ('Build-Nginix') {
               checkout scm
                                   }
                 }
            } 
       
        stage ('NginxDeployment')
        {
           steps {
              node ('Build-Nginix')
                   {
                sh 'sudo cp /home/ubuntu/workspace/MyPipelinejob1/* /var/www/html/ '             
                   }
                 } 
        }
    }
}
