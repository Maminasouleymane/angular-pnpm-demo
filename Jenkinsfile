pipeline {
    
  agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }  

  
    environment {
        CI = 'true' 
    }
    
    stages {
        stage('Build') {
            steps {
                script {
                    def npmInstallStartTime = System.currentTimeMillis()
                    sh 'npm install'
                    def npmInstallTime = System.currentTimeMillis() - npmInstallStartTime
                    echo "npm install took ${npmInstallTime}ms"

                    def ngBuildStartTime = System.currentTimeMillis()
                    sh 'ng build'
                    def ngBuildTime = System.currentTimeMillis() - ngBuildStartTime
                    echo "ng build took ${ngBuildTime}ms"
                }
            }
        }
    }
}
