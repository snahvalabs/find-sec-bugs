node('docker') {
    checkout scm
    stage('Build') {
        docker.withRegistry('https://hub.softwaresecured.com') {
            def image = docker.image('hub.softwaresecured.com/xbuntu:latest')
                image.pull()
                image.inside('-v /var/run/docker.sock:/var/run/docker.sock:rw -v .m2:/root/.m2:rw') {
                sh 'AWS_REGION=ca-central-1 mvn clean compile deploy'
            }
        }
    }
}
