pipeline {
    agent { label '10.100.30.83' }
    stages {
        stage('Clone repository') {
            steps {
                dir('/home/raviteja') {
                git branch: 'main', credentialsId: '56513d36-0bf7-4771-849c-1640f4d97c1d', url: 'https://github.com/CT-RaviTeja66/Signupform.git'               }   
            }
        }       
        stage('Build') {
            steps {
                sh """
                    hostname
                    cd '/home/raviteja'
                    ls
                """
            }
        }
        
        // Add more stages for your pipeline
        // ...
    }
}
