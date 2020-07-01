#!groovy
pipeline {
   agent any

   tools { 
        maven 'maven3' 
    }

   stages {
      
      stage('Verificando MVN') {
        steps {
            sh "mvn -version"           
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