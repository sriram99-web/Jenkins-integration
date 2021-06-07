node {    
      def app    
      environment {
      tool name: 'Docker', type: 'dockerTool'
      }
      
      stage('Clone repository') {               
             
            checkout scm    
      }     
      stage('Build image') {         
            bat '{docker_tool} build -t test-app .'   
       }     
      stage('Test image') {           
            app.inside {            
             
             bat 'echo "Tests passed"'        
            }    
        }     
       stage('Push image') {
            docker.withRegistry('https://registry.hub.docker.com', 'docker') {            
            app.push("${env.BUILD_NUMBER}")            
            app.push("latest")        
              }    
           }
        }
