
node('linux') {
        stage('Setup') {
                git credentialsId: 'gitcredential', url: 'https://github.com/Tafessek/testrepo.git'
                sh 'echo git is connected'
        }
        stage('Build') {
                sh 'docker build -t hello-world:1.0 .'
        }
        stage('Test') {
                sh 'docker stop hello-world:1.0 || true'
                sh 'docker rm hello-world || true'
                sh 'docker run -d --name web1 -p 80:80 --env PHP_PORT=80 hello-world:1.0'
               
        }
}
