pipeline {
    agent any
    stages {
//        stage('Compile Stage') {
//
//            steps {
//                withEnv(["JAVA_HOME=${tool name: 'java8', type: 'jdk'}"]) {
//
//                    withMaven(maven: 'apache-maven-3.6.3') {
//                        bat 'mvn clean compile'
//                    }
//                }
//            }
//        }
//        stage('Testing Stage') {
//            steps {
//                withEnv(["JAVA_HOME=${tool name: 'java8', type: 'jdk'}"]) {
//                    withMaven(maven: 'apache-maven-3.6.3') {
//                        bat 'mvn test'
//                    }
//                }
//            }
//        }
//        stage('Install Stage') {
//            steps {
//                withEnv(["JAVA_HOME=${tool name: 'java8', type: 'jdk'}"]) {
//                    withMaven(maven: 'apache-maven-3.6.3') {
//                        bat 'mvn install'
//                    }
//                }
//            }
//        }
        stage('Build war file') {
            steps {
                withEnv(["JAVA_HOME=${tool name: 'java8', type: 'jdk'}"]) {
                    withMaven(maven: 'apache-maven-3.6.3') {
                        bat 'mvn clean package'
                    }
                }
            }
        }
//        stage('Build Docker Image') {
//            steps {
//                // bat 'docker build -t dcedannoruwa/test-app .'
//                bat 'docker build -t dcedannoruwa/test-app .'
//
//
//            }
//        }
//        stage('view Docker Images') {
//            steps {
//
//                bat 'docker images'
//
//            }
//        }
//        stage('Docker Login') {
//            steps {
//                withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerPwd')]) {
//                    bat "docker login -u dcedannoruwa -p ${dockerPwd}"
//                }
//            }
//        }
//        stage('Push Docker Image') {
//            steps {
//                bat 'docker push dcedannoruwa/test-app'
//
//            }
//        }
//        stage('Deploy To Tomcat') {
//            steps {
//                bat 'ADD target/test-app.war test-app.war'
//
//            }
//        }
        stage('Deploy Project To Tomcat Server') {
            steps {
                withCredentials([string(credentialsId: 'dev-server', variable: 'dev_server')]) {
                    withCredentials([string(credentialsId: 'ssh_server', variable: 'ssh_server')]) {
                        bat "pscp -r -pw ${dev_server} -hostkey ${ssh_server} target/test-app.war root@192.168.1.170:/usr/local/tomcat9/webapps"
                    }
                }
            }


        }

    }
}
