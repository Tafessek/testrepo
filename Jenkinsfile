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
                sh 'docker run -d --name web2 -p 80:80 --env NGINX_PORT=80 web1:1.0'
		sh 'curl -s $(docker inspect --format="{{.NetworkSettings.IPAddress}}" web2)'     
      }               
}
