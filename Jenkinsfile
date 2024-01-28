pipeline {
    agent any
    stages {
        stage ('checkout') {
            steps {
                checkout scm
            }
        }
        
        stage ('test') {
            steps {
                sh 'sudo npm install'
                // sh 'sudo apt install npm'
            }
        }

        stage ('build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('deploy') {
            steps {
                script {
                    // Copy built artifacts to your EC2 instance
                    sh 'scp -r -v -i /home/kalyan/kalyan/AWS/Key_Pairs/MyKeyPair.pem ./build/* ec2-user@172.31.34.78:/home/ubuntu/my-projects/react-jenkins-cicd-aws'
                }
            }
        }
    }
}
