pipeline {
   
  agent any

    stages {
        stage('Build-with-npm') {
            steps {
                nodejs('NodeJs') {
                    echo 'building with npm ...'
                    script {
                        def npmInstallStartTime = System.currentTimeMillis()
                        sh 'npm install'
                        def npmInstallTime = System.currentTimeMillis() - npmInstallStartTime
                        echo "npm install took ${npmInstallTime}ms"

                        def ngBuildStartTime = System.currentTimeMillis()
                        sh 'npm run build'
                        def ngBuildTime = System.currentTimeMillis() - ngBuildStartTime
                        echo "ng build took ${ngBuildTime}ms"
                    }
                }
            }
        }
        stage('Build-with-pnpm') {
            steps {
                nodejs('NodeJs') {
                    echo 'building with pnpm ...'
                    script {
                        def pnpmInstallStartTime = System.currentTimeMillis()
                        sh 'corepack enable'
                        sh 'corepack prepare pnpm@latest-9 --activate'
                        sh 'pnpm install'
                        sh 'npm install'
                        def pnpmInstallTime = System.currentTimeMillis() - pnpmInstallStartTime
                        echo "npm install took ${pnpmInstallTime}ms"

                        def ngBuildStartTime = System.currentTimeMillis()
                        sh 'npm run build'
                        def ngBuildTime = System.currentTimeMillis() - ngBuildStartTime
                        echo "ng build took ${ngBuildTime}ms"
                    }
                }
            }
        }
    }
}
