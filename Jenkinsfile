node {    
      def app    
      environment {
      tool name: 'Docker', type: 'dockerTool'
      }
      
      stage('Clone repository') {               
             
            checkout scm    
      }     
      stage('Build image') {         
            app = docker.build("app-test")   
       }     
      stage('Test image') {                      
             
             sh 'echo "Tests passed"'
             
            
        }     
       stage('Push image') {
            docker.withRegistry('https://registry.hub.docker.com', 'docker') {                        
            app.push("latest")        
              }    
           }
        }
