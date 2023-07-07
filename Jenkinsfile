pipeline {
    agent any
    tools {nodejs "nodejs"}
    environment {
        CUSTOMER_SERVICE_API = "http://localhost:8001/api/customer"
        PRODUCTS_SERVICE_API = "http://localhost:8002/api/products"
    }
    stages {
        stage('build stage') {
            steps {
                git branch: 'dev', url: 'https://github.com/rizkypanz16/jenkins-reactjs-project.git'
                sh '''
                echo "build stage"
                git checkout -- .
                git pull origin dev
                ls
                npm install
                npm run build
                pm2 start ecosystem.config.js
                '''
            }
        }
    }
    post{
        success{
            echo 'build success'
        }
        failure{
            echo 'build failure'
        }
    }
}