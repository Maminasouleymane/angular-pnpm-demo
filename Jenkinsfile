pipeline {
    agent any

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
