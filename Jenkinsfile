pipeline {
    agent {
        docker { image 'public.ecr.aws/docker/library/maven:3.9-sapmachine' }
    }
    stages {
        stage('Source') {
            steps {
                sh 'mvn --version'
                sh 'git --version'
                git branch: 'main',
                    url: 'https://github.com/hitesh24by365/04_03-docker-agent.git'
            }
        }
        stage('Clean') {
            steps {
                dir("${env.WORKSPACE}"){
                    sh 'mvn clean'
                }
            }
        }
        stage('Test') {
            steps {
                dir("${env.WORKSPACE}"){
                    sh 'mvn test'
                }
            }
        }
        stage('Package') {
            steps {
                dir("${env.WORKSPACE}"){
                    sh 'mvn package -DskipTests'
                }
            }
        }
    }
}
