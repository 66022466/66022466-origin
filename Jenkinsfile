                     pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
				//แก้ตรง team33-neogym ให้เป็นชื่อเดียวกับ pipeline job/item ที่สร้างใน jenkins
                sh "scp -r /var/lib/jenkins/workspace/team1-boxer/* root@54.169.203.45:~/team1-boxer"                 
            }
        }
        
        stage("Build Docker Image") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/team1-boxer/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/team1-boxer/playbooks/deploy.yaml'
            }    
        } 
    }
}
