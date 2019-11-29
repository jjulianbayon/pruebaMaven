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
        stage ('Start inicio release'){
            try{
                steps {
                    sh '''
                        echo comenzando versión
                    '''

                    sh "mvn -X gitflow:release-start"

                    }
                }
            catch (exc) {
            println "Fallo en la  compilación- ${currentBuild.fullDisplayName}"
            throw (exc)
            }    
            
        }
        stage ('Build') {
            steps {
                echo 'Primer pipeline.'
            }
        }
    }
}