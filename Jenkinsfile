pipeline { 
    agent any stages { 
        stage('Clone Repository') { 
            steps { git 'https://github.com/shadow630/Assignment1_Devops.git' } } 
        stage('Build and Test') { 
                steps { sh 'mvn clean install' } } 
        stage('Deploy to Tomcat server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'ea592646-15c0-427b-810d-b48273d322c6', path: '', url: 'http://localhost:8080')],
                 contextPath: null, war: '**/*.war'
            }

        }
        stage('Restart Server') { 
            steps { sshagent(['']) { 
                sh 'ssh @ "sudo systemctl restart "' } 
                  }
                                  }  
                 
                 
                    } 
                 
         }
