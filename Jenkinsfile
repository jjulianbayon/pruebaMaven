#!groovy

    stage('Compile') {
        
            
                    sh "echo Compiling"
                    sh "mvn -B compile "
                
            }
      
    stage   ('Cache') {
             
                    sh "echo Updating Caches"
                    uploadCache key:cache_name, paths:[maven_local_repo]
                
            }       


    stage('Test') {
       
                    sh "echo Running coverage"
                    sh "mvn -B scoverage:report "
                    stash name: 'coverage', includes: 'target/scoverage.xml'
                
            }

