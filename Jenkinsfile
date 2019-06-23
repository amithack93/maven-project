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
                echo "Maven Success"
            }
            post {
                success {
                    echo "The Checkstyle Analysis Result"
                    checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '**/checkstyle-result.xml', unHealthy: ''
                    echo "The Archive Artifact"
                    archiveArtifacts '**/*.war'
                    echo "Junit Test Report"
                    junit '**/surefire-reports/*.xml'
                    echo "Build Process Success"
                }
            }
        }
        stage ('Deploy') {
            steps {
                echo "This is Deployment Satge"
            }
        }
    }
}