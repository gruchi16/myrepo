pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello my World'

                echo "Build number is ${env.BUILD_NUMBER}"
                echo "Build number is ${env.GIT_TAG}"
            }
        }

        
    }
}
