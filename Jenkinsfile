node('linux') {
        stage('Setup') {
                git credentialsId: 'gitcredential', url: 'https://github.com/Tafessek/testrepo.git'
                sh 'echo git is connected'
        }
        stage('Build') {
                sh 'docker build -t web1:1.0 .'
        }
        stage('Test') {
                sh 'docker stop web2 || true'
                sh 'docker rm web2 || true'
                sh 'docker run -d --name web2 -P web1:1.0'
		     
      }               
}
