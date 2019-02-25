def remote = [:]
def isSudo = true
remote.name = "node1"
remote.host = "ajitsahu4c.mylabserver.com"
remote.allowAnyHosts = true
remote.isSudo = true

node {
    withCredentials([usernamePassword(credentialsId: 'clouduser', passwordVariable: 'password', usernameVariable: 'userName')]) {
        remote.user = userName
        remote.password = password

        stage("SSH Steps Rocks!") {
            sshPut remote: remote, from: 'test.sh', into: '.'
            sshCommand remote: remote, command: 'sh test.sh', sudo: isSudo
        }
    }
}
