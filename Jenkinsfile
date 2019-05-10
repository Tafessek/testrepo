
node('linux') {
        stage('Setup') {
                git credentialsId: 'gitcredential', url: 'https://github.com/Tafessek/testrepo.git'
                sh 'echo git is connected'
        }
        stage('Build') {
                sh 'docker build -t web2:1.0 .'
        }
        stage('Test') {
                sh 'docker run -d --name web3 -p 80:80 --env PHP_PORT=80 web1:2.0'
               
        }
        stage('Remove') {
                sh 'docker stop web3 || true'
                sh 'docker rm web3 || true'
        }        
        
}
