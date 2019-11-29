#!groovy
pipeline {
    agent any
    tools { 
        maven 'Maven 3.3.9' 
        jdk 'jdk8' 
    }
    stages {
        stage ('Iniciando Variables') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }
        
        stage ('Build') {
            steps {
                echo 'Primer pipeline'
            }
        }
        stage('Compile') {
        try {
                    sh "echo Compiling"
                    sh "mvn -X gitflow:release-start package"
                }
            }
        }
        catch (exc) {
            println "Failed to compile - ${currentBuild.fullDisplayName}"
            throw (exc)
        }
        
    }
}