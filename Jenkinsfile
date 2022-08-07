pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ponnamnagesh/TwotierRDS']]])            

          }
        }    
        stage ("Terraform Init") {
            steps {
                sh ('terraform init') 
            }
        }
        stage ("Terraform Plan") {
            steps {
                sh ('terraform plan') 
            }
        }
        stage ("Terraform Action") {
            steps {
                echo "Terraform action is --> ${action}"
                //sh ('terraform ${action} --auto-approve')
                sh ('terraform ${action} --auto-approve -var-file="secrets.tfvars')
                //sh ('terraform apply --auto-approve') 
                //sh ('terraform destroy --auto-approve')
           }
        }
    }
}
