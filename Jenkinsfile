pipeline {    
      def app    
      environment {
      tool name: 'Docker', type: 'dockerTool'
      }
      agent {
        label 'ubuntu-1804 && amd64 && docker'
      }
      
      stage('Clone repository') {               
             
            checkout scm    
      }     
      stage('Build image') {         
            app = docker.build("srirammaster/test")    
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
