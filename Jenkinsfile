def remote = [:]
remote.name = "node1"
remote.host = "ajitsahu3c.mylabserver.com"
remote.allowAnyHosts = true
remote.isSudo = true

node {
    withCredentials([usernamePassword(credentialsId: 'clouduser', passwordVariable: 'password', usernameVariable: 'userName')]) {
        remote.user = userName
        remote.password = password

        stage("SSH Steps Rocks!") {
            writeFile file: 'test.sh', text: 'ls'
            sshCommand remote: remote, command: 'mkdir -p /usr/local/clouduser', isSudo
            sshScript remote: remote, script: 'test.sh'
            sshPut remote: remote, from: 'test.sh', into: '.'
            sshGet remote: remote, from: 'test.sh', into: 'test_new.sh', override: true
        }
    }
}
