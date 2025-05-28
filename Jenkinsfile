pipeline {
    agent any

    tools {
        maven 'Maven 3.8.5'
        jdk 'JDK11'
    }

    environment {
        DEPLOY_DIR = "/opt/tomcat/webapps"
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/vishnuminnu/petclinic-ci'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                sh 'scp -i /var/lib/jenkins/.ssh/project-2.pem target/*.war ubuntu@174.129.142.39:/opt/tomcat/webapps/petclinic.war'
            }
        }
    }
}
