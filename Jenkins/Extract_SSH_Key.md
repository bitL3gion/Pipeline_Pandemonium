```
stage('sshUserPrivateKey') {
      steps {
        script {
          withCredentials([
            sshUserPrivateKey(
              credentialsId: 'production-bastion',
              keyFileVariable: 'keyFile',
              passphraseVariable: 'passphrase',
              usernameVariable: 'username')
          ]) {
            print 'keyFile=' + keyFile
            print 'passphrase=' + passphrase
            print 'username=' + username
            print 'keyFile.collect { it }=' + keyFile.collect { it }
            print 'passphrase.collect { it }=' + passphrase.collect { it }
            print 'username.collect { it }=' + username.collect { it }
            print 'keyFileContent=' + readFile(keyFile)
          }
        }
      }
    }
```
