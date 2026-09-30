pipeline {
    agent none

    environment {
        BACKEND_BUILD_IMAGE = 'maven:3.9-eclipse-temurin-17'
        MONGO_IMAGE         = 'mongo:7'
        CI_NETWORK          = "product-service-ci-${BUILD_NUMBER}"
        MONGO_CONTAINER     = "mongo-${BUILD_NUMBER}"
        MONGODB_URI         = "mongodb://mongo-${BUILD_NUMBER}:27017/products_db"
    }

    stages {
        stage('Init') {
            agent any
            steps {
                echo 'Environment configured — stages come next'
            }
        }
    }
}
