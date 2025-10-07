pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'
    }
    stages {
        stage('Clean') {
            steps {
                // Just clean the project, no manual git clone needed
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
    post {
        success {
            mail to: 'akulayashwanth43@gmail.com',
                 subject: "SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                 body: "Good news! The build ${env.BUILD_NUMBER} of job ${env.JOB_NAME} succeeded.\nCheck console output at ${env.BUILD_URL}."
        }
        failure {
            mail to: 'akulayashwanth43@gmail.com',
                 subject: "FAILURE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                 body: "Alert! The build ${env.BUILD_NUMBER} of job ${env.JOB_NAME} failed.\nCheck console output at ${env.BUILD_URL}."
        }
        unstable {
            mail to: 'akulayashwanth43@gmail.com',
                 subject: "UNSTABLE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                 body: "Warning! The build ${env.BUILD_NUMBER} of job ${env.JOB_NAME} is unstable.\nCheck console output at ${env.BUILD_URL}."
        }
    }
}
