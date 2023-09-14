pipeline {
    agent { label 'teja10.100.30.83' }
    stages {  
        stage('Clone repository') {
            environment {
                GIT_SSH_COMMAND="ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no"
            }
            steps {
               dir('/home/teja/test5/') {
                    echo "started"
                    git branch: 'main', credentialsId: 'teja', url: 'https://github.com/CT-RaviTeja66/Signupform.git'
                    echo "completed"
                }
            }
        }
        stage('Build') {
            steps {
               sh """ 
                  cp /home/teja/test5/* /home/teja/test6/
                """
            }
        }
        stage('S3download') {
            steps {
                script {
                    FAILED_STAGE=env.STAGE_NAME
                    def s3Bucket = 'ct-sample'
                    def s3Key = 'chat.php'
                    def localFilePath = '/home/teja/s3_data'
            
                    withAWS(credentials: 's3_ct-sample') {
                        sh "aws s3 cp s3://${s3Bucket}/${s3Key} ${localFilePath}"
                    }
            
                    echo "Downloaded file from S3 and saved it to ${localFilePath}" 
                }
            }
        }

    }
    // post {
    //     success {
    //         mail to: "raviteja.g@cartrade.com,graviteja9866@gmail.com",
    //         subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
    //         body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
    //     } 
    //     failure {
    //         mail to: "raviteja.g@cartrade.com,graviteja9866@gmail.com",
    //         subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
    //         body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL} Failed stage at: ${FAILED_STAGE}"
    //         echo "Failed stage name: ${FAILED_STAGE}"
    //     }
    // }  
}
