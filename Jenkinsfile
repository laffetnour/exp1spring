pipeline {
    agent any

    tools {
        maven 'maven' 
    }

    stages {
        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }

        stage('Clone Repository') {
            steps {
                sh 'git clone https://github.com/laffetnour/exp1spring.git'
            }
        }

        stage('Build with Maven') {
            steps {
                dir('exp1spring') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('exp1spring') {
                    sh 'docker build -t hello-world .'
                }
            }
        }

        stage('Run Docker Compose') {
            steps {
                dir('exp1spring') {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
