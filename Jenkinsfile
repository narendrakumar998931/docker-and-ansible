pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('clone'){
            steps{
                git 'https://github.com/narendrakumar998931/pratice.git'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('ansible playbook'){
            steps{
                ansiblePlaybook credentialsId: 'node2', disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'install.yml'
            }
        }
        stage('docker file excution'){
            steps{
                sh 'docker build -t bnani/web .'
            }
        }
        stage('run the container'){
            steps{
                sh 'docker run -tid --name=web -p 8000:8080 bnani/web'
            }
        }
    }
}
