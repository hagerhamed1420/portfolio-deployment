# Portfolio Website with Jenkins CI/CD

This is my personal portfolio website with automated deployment using Jenkins.

## Technologies Used
- HTML5, CSS3, JavaScript
- Apache HTTP Server
- Jenkins CI/CD
- GitHub
- Fedora Linux

## Project Structure
```
portfolio-template/
├── templatemo_578_first_portfolio/  # Website template files
├── Jenkinsfile                       # Jenkins pipeline configuration
└── README.md                         # This file
```

## Deployment
The website is automatically deployed to `/var/www/portfolio/` when changes are pushed to the main branch.

## Local Access
http://localhost

## Setup Steps
1. Jenkins pulls code from GitHub
2. Copies files to Apache web directory
3. Sets correct permissions
4. Restarts Apache server
5. Verifies deployment

## Author
Hager Hamed
