pipeline {
  agent any 
   stages {
    stage('pull') {
      steps {
      	script{
      	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], 
      	   userRemoteConfigs: [[ 
        credentialsId: '895dca4e-24c6-4385-9f76-e37ecb3b2270',
        url: 'https://github.com/WASSIM980/CD.git']]]);
        }
           }
  
  }
    stage("build") {
             steps {
                 sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
            }
        }
    stage("docker") {
            steps {
                sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
            }
        }  
    stage('Docker Login'){
            steps{
			
                sh 'docker login -u azizncir -p Azerty123**'
            }
        } 
    stage("Docker-Registry") {
            steps {
                sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
            }
        } 
       
  }
  }
