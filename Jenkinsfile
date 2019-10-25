node('docker') {
    checkout scm
    stage('Build') {
        docker.withRegistry('https://hub.reshiftsecurity.com') {
            def image = docker.image('hub.reshiftsecurity.com/xbuntu:latest')
                image.pull()
                image.inside("-u root --privileged -v /var/run/docker.sock:/var/run/docker.sock:rw -v $HOME/.m2:/root/.m2:rw") {
                sh 'AWS_REGION=ca-central-1 mvn clean deploy -Dmaven.test.skip=true'
            }
        }
    }
}
