pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/hagerhamed1420/portfolio-deployment.git'
            }
        }
        
        stage('Deploy') {
            steps {
                sh '''
                    # Copy files to web directory
                    sudo cp -r templatemo_578_first_portfolio/* /var/www/portfolio/
                    
                    # Set permissions
                    sudo chown -R apache:apache /var/www/portfolio
                    sudo chmod -R 755 /var/www/portfolio
                    
                    # Restart Apache
                    sudo systemctl restart httpd
                '''
            }
        }
        
        stage('Verify') {
            steps {
                sh '''
                    # Check if index.html exists
                    if [ -f /var/www/portfolio/index.html ]; then
                        echo "Deployment successful!"
                    else
                        echo "Deployment failed - index.html not found"
                        exit 1
                    fi
                '''
            }
        }
    }
    
    post {
        success {
            echo 'Portfolio deployed successfully!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
