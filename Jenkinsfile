pipeline {
    agent any
    tools {
        maven 'maven-3.8.6'
        
    }
    stages {
       
        stage("clean up") {
            steps {
                deleteDir()
            }
        }
        stage("Clone repo") {
            steps {
                sh "git clone https://github.com/laffetnour/exp1spring.git"
            }
        }
        stage("Generate backend image") {
            steps {
                dir("exp1spring") {
                    sh "mvn clean install"
                    sh "docker build -t hello-world ."
                }
            }
        }
        stage("Run docker compose") {
            steps {
                dir("exp1spring") {
                    sh "docker-compose up -d"
                }
            }
        }
    }
}
