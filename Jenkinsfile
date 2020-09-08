pipeline {
    agent any
    tools {
        maven 'apache-maven-3.5.0'
        jdk 'jdk10'
    }
    environment {
            JAVA_HOME = "${jdk}"
        }

    stages {
        stage('Compile Stage') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('QA-Sonar') {

         
            steps {
                withSonarQubeEnv('sonardocker') {

                     def scannerHome = tool 'sonar-scanner'
                     bat "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
