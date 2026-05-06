pipeline {
    agent any

    tools {
        maven 'maven'
        jdk 'jdk-21'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'YOUR_GITHUB_LINK'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        path: '',
                        url: 'http://localhost:8081'
                    )
                ],
                contextPath: 'hello-world',
                war: 'target/hello-world.war'
            }
        }
    }
}
