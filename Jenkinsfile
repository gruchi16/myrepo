pipeline {
    agent any
    parameters {
        string(name: 'version', defaultValue: '1.0.0', description: 'App version')
       
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello my World'

                echo "Build number is ${env.BUILD_NUMBER}"
                
        
        
    }
}

 stage('Extract Git Tag') {
            steps {
                script {
                    // Get the latest tag
                    def gitTag = sh(script: "git describe --tags --abbrev=0", returnStdout: true).trim()
                    echo "Git Tag: ${gitTag}"

                    // Optionally set it as an environment variable
                    env.GIT_TAG = gitTag
                }
            }
        }

        stage('Use Git Tag') {
            steps {
                echo "Using Git Tag: ${env.GIT_TAG}"
                // You can use this tag in build, deploy, etc.
            }
        }

         stage('print the parameter') {
            steps {
                echo "VERSION: ${params.version}"
            }
        }

}
}
