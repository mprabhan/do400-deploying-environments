pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    stages {
        stage('Tests') {
            steps {
                sh 'chmod +x ./mvnw ; ./mvnw clean test'
            }
        }
        stage('Package') {
            steps {
                sh '''
                    ./mvnw package -DskipTests \
                    -Dquarkus.package.type=uber-jar
                '''
                archiveArtifacts 'target/*.jar'
            }
        }
    }
}