pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.16/bin:$PATH"
    }
    stages {
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }

        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Docker uzima JAR iz istog direktorija i radi sliku lokalno
                    sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
                    
                    echo "Docker image je uspješno kreiran lokalno na Jenkins poslužitelju!"
                }
            }
        }
    }
}