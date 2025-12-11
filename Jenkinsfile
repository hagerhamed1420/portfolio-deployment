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
                    # Print current directory and files
                    pwd
                    ls -la
                    
                    # Check if template directory exists
                    if [ -d "templatemo_578_first_portfolio" ]; then
                        echo "Template directory found"
                        ls -la templatemo_578_first_portfolio/
                    else
                        echo "ERROR: Template directory not found!"
                        exit 1
                    fi
                    
                    # Copy files to web directory
                    sudo rm -rf /var/www/portfolio/*
                    sudo cp -r templatemo_578_first_portfolio/* /var/www/portfolio/
                    
                    # Set permissions
                    sudo chown -R apache:apache /var/www/portfolio
                    sudo chmod -R 755 /var/www/portfolio
                    
                    # List deployed files
                    ls -la /var/www/portfolio/
                    
                    # Restart Apache
                    sudo systemctl restart httpd
                '''
            }
        }      
       
