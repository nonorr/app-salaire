 node{
      stage('Clone') {
          checkout scm
      }
      stage('Creation user'){

          '''
          apk add sshpass
          FILE=/root/.ssh/id_rsa
          if [ -f "$FILE" ]; then
              echo "File Found"
          else
              ssh-keygen -q -t rsa -N \'\' -f /root/.ssh/id_rsa
          fi
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
