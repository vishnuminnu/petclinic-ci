pipeline {
    agent any

    tools {
        maven 'Maven 3.8.5' // Ensure Maven 3.8.5 is installed via Jenkins Global Tools
        jdk 'JDK11'         // Ensure JDK 11 is installed via Jenkins Global Tools
    }

    environment {
        DEPLOY_DIR = "/opt/tomcat/webapps"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/vishnuminnu/petclinic-ci.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                sh 'scp -i /home/vishnu/Downloads/project2.pem target/*.war ubuntu@174.129.142.39:/opt/tomcat/webapps/petclinic.war'
            }
        }
    }
}
