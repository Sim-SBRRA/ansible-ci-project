pipeline {
    agent any
    
    tools
    {
       maven "Maven"
    }
     
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/Sim-SBRRA/ansible-ci-project.git'
             
          }
        }
         stage('Tools Init') {
            steps {
                script {
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
               def tfHome = tool name: 'Ansible'
                env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
                    
            }
            }
        }
     
        
        stage('Ansible Deploy') {
             
            steps {
                 
             
               sh "ansible-playbook tomcat-setup.yml -vvv --user jenkins --key-file ~/.ssh/id_rsa"

               
            
            }
        }
    }
}
