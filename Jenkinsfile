properties([parameters([choice(choices: ['Yes', 'No', 'Maybe', 'Sure'], description: 'Please choose your deploy something ', name: 'Deploy')])])


pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                script {
                    if (params.Deploy == "Yes") {
                        echo 'Hello World'
                        input message: 'Where to Deploy', parameters: [choice(choices: ['Prod', 'Dev', 'Test', 'QA'], name: 'Where')]
                    }
                }
                sh 'echo hi'
            }
        }

        stage('Build Docker Image') {
            parallel {
                stage('First Branch') {
                    steps {
                        sh 'python main.py'
                    }
                }
                stage('Second Branch') {
                    steps {
                        echo 'Running second branch'
                        sh 'echo second'
                    }
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                echo 'Pushing to DockerHub'
                sh 'echo push'
            }
        }
    }
}
