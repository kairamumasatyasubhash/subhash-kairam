pipeline {
    agent any
    tools {
        jdk 'jdk11'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/devopswithcloud/spring-petclinic.git'
            }
        }
        stage('Code Analysis') {
            steps {
                // This single command cleans, verifies (which includes packaging), and runs Sonar analysis.
                sh '''
                    mvn clean verify sonar:sonar \
                      -Dsonar.projectKey=saya \
                      -Dsonar.host.url=http://34.29.252.159:9000 \
                      -Dsonar.login=sqp_aed602dd7db85f4c9f23d5ac321a488d51e9faf3
                '''
            }
        }
    }
}
