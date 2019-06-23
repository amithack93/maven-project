pipeline {
    agent any 
    tools {
        maven 'maven1'
        jdk  'java1.8'
    }
    stages {
        stage ('init') {
            steps {
                echo "This is Initializing Stage"
            }
        }
        stage ('build') {
            steps {
                echo "This is Build Satge"
                sh label: '', script: 'mvn clean package checkstyle:checkstyle'
            }
        }
        stage ('Deploy') {
            steps {
                echo "This is Deployment Satge"
            }
        }
    }
}