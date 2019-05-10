
node('linux') {
        stage('Setup') {
                git git credentialsId: 'gitcredential', url: 'https://github.com/Tafessek/testrepo.git'
                sh 'echo git is connected'
        }
        stage('Build') {
                sh 'docker build -t web:1.0 .'
        }
        stage('Test') {
                sh 'docker stop classweb1 || true'
                sh 'docker rm web1 || true'
                sh 'docker run -d --name web1 -p 80:80 --env PHP_PORT=80 web:1.0'
               
        }
}
