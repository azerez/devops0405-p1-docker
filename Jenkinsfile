properties([parameters([choice(choices: ['Yes', 'No', 'Maybe', 'Sure'], description: 'Please choose your deploy something ', name: 'Deploy')])])

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                scripts {
                    if (params.Deploy == "Yes"){
                    echo 'Hello World'
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

