pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                git 'https://github.com/sreejita-maitra/webapp.git'
            }
        }
        
        stage('Build') {
            steps {
                // Build your code (replace with your build commands)
                bat 'clean install' // or any other build command you use
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                // Copy the WAR file to Tomcat webapps directory
                bat 'cp target/*.war /path/to/tomcat/webapps/'
            }
            post {
                success {
                    // Restart Tomcat
                    bat '/path/to/tomcat/bin/shutdown.bat'
                    bat '/path/to/tomcat/bin/startup.bat'
                }
            
        }
    }
    
    post {
        success {
            // Show the output on browser
            echo 'Deployment successful! Application is accessible at: http://your-tomcat-server:8080/MavenWebApp'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
