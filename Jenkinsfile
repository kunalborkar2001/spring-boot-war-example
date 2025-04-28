pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage("Test Code") {
            steps {
                sh "mvn test"
                echo "========executing A========"
            }
        }

        stage("Build Code") {
            steps {
                sh "mvn package"
                echo "========executing B========"
            }
        }

        stage("Deploy to Test") {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: '4545e701-e304-46c6-87cb-b74a5f9b784b',
                        path: '',
                        url: 'http://192.168.31.89:9090'
                    )
                ],
                contextPath: '/app',
                war: '**/*.war'

                echo "========executing C========"
            }
        }
    }

    post {
        always {
            echo "========always========"
        }
        success {
            echo "========pipeline executed successfully ========"
        }
        failure {
            echo "========pipeline execution failed========"
        }
    }
}
