pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Build') {
            steps {
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
