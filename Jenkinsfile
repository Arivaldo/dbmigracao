#!groovy
pipeline {
    agent {
        docker {
            image 'maven:3.6.3-amazoncorretto-11'
            args '-v /var/jenkins_home/.m2:/root/.m2'
        }
    }

    stages {
                
        stage('Verificando MVN') {
            steps {
                sh "mvn -version"           
            }
        }
        stage('Executando Flyway') {
            steps {
                sh 'mvn flyway:migrate'
            }
        }
        stage('Registro ITSM') {
            steps {
                sh 'curl -vk -H "Content-Type: application/json" -d {"name":"test","salary":"123","age":"23"} http://dummy.restapiexample.com/create'
            }
        }   
    }
}