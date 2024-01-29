pipeline {
    agent any

    environment {
        EC2_HOST = '172.31.34.78'
        EC2_USER = 'ec2-user'
        EC2_KEY_CREDENTIAL = 'MyKeyPair'
    }

    stages {
        stage ('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage ('Install') {
            steps {
                sh 'sudo npm install'
            }
        }

        stage ('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'scp -r -v -i /home/kalyan/kalyan/AWS/Key_Pairs/MyKeyPair.pem ./build/* ec2-user@172.31.34.78:/home/ubuntu/my-projects/react-jenkins-cicd-aws'
                }
                //  script {
                //     withCredentials([sshUserPrivateKey(credentialsId: EC2_KEY_CREDENTIAL, keyFileVariable: 'EC2_KEY_FILE')]) {
                //         sh "scp -r -o StrictHostKeyChecking=no -i $EC2_KEY_FILE ./build/* $EC2_USER@$EC2_HOST:/home/ubuntu/my-projects/react-jenkins-cicd-aws"
                //     }
                // }
            }
        }
    }
}
