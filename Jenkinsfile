#!groovy
pipeline {
    agent {
        docker {
            image 'maven:3.6.3-amazoncorretto-11'
            args '-v /var/jenkins_home/.m2:/root/.m2'
        }
    }

    parameters {
        string(name: 'HOST', defaultValue: 'scs0000', description: 'Nome DNS do host')

        text(name: 'DESCRICAO', defaultValue: 'O proposito é ...', description: 'Propósito do serviço/servidor')

        booleanParam(name: 'Para Base de Dados?! ', defaultValue: false, description: 'Marque se for para SGBD')

        choice(name: 'TAMANHO', choices: ['Pequeno', 'Médio', 'Grande'], description: 'Tamanho do Host')

        password(name: 'PASSWORD', defaultValue: 'Senha segura', description: 'Coloque o password')
    }

    stages {
                
        stage('Verificando MVN e Parametros de entrada') {
            steps {
                sh "mvn -version"    

                echo "O nome do Host é ${params.HOST}"

                echo "Descrição: ${params.DESCRICAO}"

                echo "Será usado para Database: ${params.TOGGLE}"

                echo "Tamanho: ${params.TAMANHO}"

                echo "Password: ${params.PASSWORD}"       
            }
        }
        stage('Executando Flyway') {
            steps {
                sh 'mvn flyway:migrate'
            }
        }
        stage('Registro ITSM') {
            steps {
                sh 'curl -vk -H "Content-Type: application/json" -d {"name":"test","salary":"123","age":"23"} http://dummy.restapiexample.com/api/v1/create'
            }
        }   
    }
}