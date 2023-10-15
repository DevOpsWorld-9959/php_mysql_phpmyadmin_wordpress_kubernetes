pipeline {
    agent any

    stages {
        stage('GitCheckout') {
            steps {
                git branch: 'main', url: 'https://github.com/DevOpsWorld-9959/php_mysql_phpmyadmin_wordpress_kubernetes.git'
            }
        }
        stage("Deploying Volumes&Secretes"){
            steps{
                sh '''echo test | sudo -S  kubectl apply -f mysql-pv.yaml
                    echo test | sudo -S  kubectl apply  -f  mysql-pvc.yaml
                    echo test | sudo -S  kubectl apply -f mysql-database-secrete.yaml
                    echo test | sudo -S  kubectl apply -f mysql-user-pass-secret.yaml
                    echo test | sudo -S  kubectl apply -f mysql_root_password_secret.yaml'''
            }
        }
        stage("Deploying Mysql"){
            steps{
               sh 'echo test | sudo -S kubectl apply -f mysql_deployement.yaml'
            }
        }
        stage("Deploying Phpmyadmin"){
            steps{
                sh 'echo test | sudo -S kubectl apply -f phpmyadmin_deployment.yaml'
            }
        }
        stage("Deploying wordpress"){
            steps{
                sh 'echo test | sudo -S kubectl apply -f wordpress_deployment.yaml'
            }
        }      
        
    }
}
