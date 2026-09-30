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
        stage('Build: Backend Services') {
            parallel {
                stage('discovery-server') {
                    agent {
                        docker {
                            image "${BACKEND_BUILD_IMAGE}"
                            args '-v maven-repo:/root/.m2'
                        }
                    }
                    steps {
                        checkout scm
                        dir('discovery-server') {
                            sh 'mvn -B -DskipTests clean package'
                        }
                    }
                }
                stage('user-service') {
                    agent {
                        docker {
                            image "${BACKEND_BUILD_IMAGE}"
                            args '-v maven-repo:/root/.m2'
                        }
                    }
                    steps {
                        checkout scm
                        dir('user-service') {
                            sh 'mvn -B -DskipTests clean package'
                        }
                    }
                }
                stage('product-service') {
                    agent {
                        docker {
                            image "${BACKEND_BUILD_IMAGE}"
                            args '-v maven-repo:/root/.m2'
                        }
                    }
                    steps {
                        checkout scm
                        dir('product-service') {
                            sh 'mvn -B -DskipTests clean package'
                        }
                    }
                }
                stage('media-service') {
                    agent {
                        docker {
                            image "${BACKEND_BUILD_IMAGE}"
                            args '-v maven-repo:/root/.m2'
                        }
                    }
                    steps {
                        checkout scm
                        dir('media-service') {
                            sh 'mvn -B -DskipTests clean package'
                        }
                    }
                }
                stage('api-gateway') {
                    agent {
                        docker {
                            image "${BACKEND_BUILD_IMAGE}"
                            args '-v maven-repo:/root/.m2'
                        }
                    }
                    steps {
                        checkout scm
                        dir('api-gateway') {
                            sh 'mvn -B -DskipTests clean package'
                        }
                    }
                }
            }
        }
    }
}
