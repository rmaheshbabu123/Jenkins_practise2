pipeline 
{   
   agent {
     label 'Build-Nginix'
         } 
   parameters {
           choice(choices: 'dev\nsyst\nmaster', description: 'Enter Branch Name ' , name: 'Branch_Name')    
    }

   if ("${Branch_Name}" == 'dev')  
          {
            Checkout()   //  cloning 
            NginxDeployment() // for k8s deployment
      }
} 

def Checkout()   
{ 
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
     } 
}
             
 def NginxDeployment() {       
        stage ('NginxDeployment')
        {
           steps {
              node ('Build-Nginix')
                   {
                sh 'sudo cp /home/ubuntu/workspace/MyPipelinejob2/* /var/www/html/ '             
                   }
                 } 
        }
    }
}
