pipeline {
    agent any
tools {
    maven 'M2_HOME'
}
    stages {
        stage ('Build') {
            steps {
                'mvn clean package'
            }
            post {
                success {
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/tagget/*.war'
                }
            }

        }
        stage ('Deploy to Tomcat server'){
            steps {
                deploy adapters: [tomcat9(credentialsId: 'ea592646-15c0-427b-810d-b48273d322c6', path: '', url: 'http://localhost:8080')], contextPath: null, war: '**/*.war'
            }

        }
    }
}
