pipeline {
  agent any 
   stages {
    stage('pull') {
      steps {
      	script{
      	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], 
      	   userRemoteConfigs: [[ 
        credentialsId: 'a0f817ce-4469-4369-af77-9e4461df8fd1',
        url: 'https://github.com/aziz2772/CD.git']]]);
        }
           }
  
  }
    stage("build") {
             steps {
                 sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
            }
        }
  }
  }
