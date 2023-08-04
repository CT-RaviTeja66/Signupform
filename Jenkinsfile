pipeline {
    agent { label 'ravi 10.100.30.83' }
        stage('Clone repository') {
            steps {
                dir('/data/vhosts/localhost/httpdocs/raviteja/') {
                git branch: 'main', credentialsId: '1c3fe346-10e7-4dc5-b55c-b6d40ff50124', url: 'https://github.com/CT-RaviTeja66/Signupform.git'   
               }
           }    
        }
}
