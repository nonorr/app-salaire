 node{
      stage('Clone') {
          checkout scm
      }
      stage('connexion'){

          '''
          apk add sshpass
          ssh-keygen -q -t rsa -N \'\' -f /root/.ssh/id_rsa
          sshpass -p \'admin\' ssh-copy-id  -o stricthostkeychecking=no root@app-salaire.rais-nordine.form
          '''
      }
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
