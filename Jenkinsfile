#!groovy

    stage('Compile') {
        try {
            
                    sh "echo Compiling"
                    sh "mvn -B compile "
                
            }
        }
        catch (exc) {
            println "Failed to compile - ${currentBuild.fullDisplayName}"
            throw (exc)
        }
        try {
             {
                    sh "echo Updating Caches"
                    uploadCache key:cache_name, paths:[maven_local_repo]
                
            }
        }
        catch (exc) {
            println "Failed to update caches - ${currentBuild.fullDisplayName}"
        }
    }


    stage('Test') {
        try {
            
                    sh "echo Running coverage"
                    sh "mvn -B scoverage:report "
                    stash name: 'coverage', includes: 'target/scoverage.xml'
                
            }
        }
        catch (exc) {
            println "Failed to test - ${currentBuild.fullDisplayName}"
            throw (exc)
        }
    }

