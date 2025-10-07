pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'
    }
    stages {
        stage('Git clone & Clean') {
            steps {
                // Remove old folder if exists (optional)
                // bat 'rmdir /s /q SE-Week4.Projects || echo Folder does not exist'
                bat 'git clone https://github.com/vd-007-b/SE-Week4.Projects.git'
                bat 'mvn clean -f SE-Week4.Projects/pom.xml'
            }
        }
        stage('Install') {
            steps {
                bat 'mvn install -f SE-Week4.Projects/pom.xml'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test -f SE-Week4.Projects/pom.xml'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package -f SE-Week4.Projects/pom.xml'
            }
        }
    }
}
