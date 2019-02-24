def remote = [:]
def isSudo = true
remote.name = "node1"
remote.host = "ajitsahu3c.mylabserver.com"
remote.allowAnyHosts = true
remote.isSudo = true

node {
    withCredentials([usernamePassword(credentialsId: 'clouduser', passwordVariable: 'password', usernameVariable: 'userName')]) {
        remote.user = userName
        remote.password = password

        stage("SSH Steps Rocks!") {
            sshCommand remote: remote, command: 'mkdir -p /usr/local/jenkins', sudo: isSudo
            sshPut remote: remote, from: 'test.sh', into: '/usr/local/jenkins/'
            sshCommand remote: remote, command: 'sh /usr/local/jenkins/test.sh', sudo: isSudo
            sshRemove remote: remote, path: '/usr/local/jenkins/test.sh'
        }
    }
}
