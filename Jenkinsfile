  
import groovy.json.JsonOutput
import groovy.transform.Field
import groovy.json.JsonSlurper

node ('Build-Nginix') 
{
   parameters {
           choice(choices: 'dev\nsyst\nmaster', description: 'Enter Branch Name ' , name: 'Branch_Name')    
    }

   if ("${Branch_Name}" == 'dev')  
          {
            Checkout()   //  checkout
            NginxDeployment() //  deployment
          }
    else if ("${Branch_Name}" == 'syst')
           {
              Checkout()   //  cloning 
              NginxDeployment() //  deployment
            }
    else if ("${Branch_Name}" == 'master') {
              Checkout()   //  cloning 
              NginxDeployment() // deployment
        }
} 

def Checkout()   
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
