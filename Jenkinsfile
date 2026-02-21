pipeline{
    agent any

    environment{
        DEMO = 'DEMO 1.0'
    }

    stages{
        stage('Build'){
            steps{
                echo "Building $BUILD_NUMBER of ${DEMO}..."

                sh '''
                echo "Using a multi-line step chmod +x ./test.sh 
                ./test.sh"
                '''
            }
        }
    }
}