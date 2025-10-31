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

      
         

        stage('Email Test') {
            steps {
                script {
                    emailext (
                        subject: "Test Email from Jenkins",
                        body: """   Build completed successfully.
                                    View build details: ${env.BUILD_URL}
                                    Please approve.""",
                        
                        from: "gruchi16@gmail.com",
                          replyTo: "gruchi16@gmail.com",
                        to: "gruchi16@gmail.com"
                    )
                }
            }
        }
   stage('Approval') {
        steps {
                script {
                    def userInput = input(
                        id: 'Approval', message: 'Do you want to proceed to deployment?',
                        parameters: [
                            choice(name: 'Proceed', choices: ['Yes', 'No'], description: 'Select Yes to continue')
                        ],
                        submitter: 'vipin',
                        submitterParameter: 'approvedBy'
                    )
                    if (userInput == 'No') {
                        error("Deployment aborted by user.")
                    }
                }
            }
        }
}
}
