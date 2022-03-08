pipeline {
    agent any
    stages {
        stage('Build') {
            agent { 
                docker {
                    label 'docker'
                    image 'maven:3.6.3-jdk-11' 
                }
            } 
            steps {
                echo 'Hello, Maven'
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Run') {
            agent { 
                docker {
                    label 'docker'
                    image 'openjdk:11.0.7-jdk-slim' 
                } 
            }
            steps {
                echo 'Hello, JDK'
                sh 'java -jar target/demodocker-0.0.1-SNAPSHOT.jar'
            }
        }
    }
}
