#!groovy
pipeline {
   agent any

   stages {
      
      stage('Verificando MVN') {
        steps {
            withMaven(maven: 'maven3') {

                // Run the maven build
                sh "mvn -version"
            }
        }
      }
      stage('Executando Flyway') {
        steps {
            ansiblePlaybook playbook: './playbook_2.yml', installation: 'ansible',  colorized: true
        }
      }
      stage('Registro ITSM') {
        steps {
            ansiblePlaybook playbook: './playbook_3.yml', installation: 'ansible',  colorized: true
        }
      }
      
      
   }
}