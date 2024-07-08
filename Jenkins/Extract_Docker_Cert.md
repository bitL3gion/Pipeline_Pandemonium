```
pipeline {
  agent any
  stages {
    stage('dockerCert') {
      steps {
        script {
          withCredentials([
            dockerCert(
              credentialsId: 'production-docker-ee-certificate',
              variable: 'DOCKER_CERT_PATH')
          ]) {
            print 'DOCKER_CERT_PATH=' + DOCKER_CERT_PATH
            print 'DOCKER_CERT_PATH.collect { it }=' + DOCKER_CERT_PATH.collect { it }
            print 'DOCKER_CERT_PATH/ca.pem=' + readFile("$DOCKER_CERT_PATH/ca.pem")
            print 'DOCKER_CERT_PATH/cert.pem=' + readFile("$DOCKER_CERT_PATH/cert.pem")
            print 'DOCKER_CERT_PATH/key.pem=' + readFile("$DOCKER_CERT_PATH/key.pem")
          }
        }
      }
    }
```
