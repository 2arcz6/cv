pipeline {
    agent any

    environment {

        REPO                    = "docker-registry.valhallaonlineservices.com"
        IMAGE                   = "${REPO}/newcampus/frontend"

        TAG_ID                  = sh(returnStdout: true, script: "git log -1 --oneline --pretty=%h").trim()
        GIT_COMMITTER_NAME      = sh(returnStdout: true, script: "git show -s --pretty=%an").trim()
        GIT_MESSAGE             = sh(returnStdout: true, script: "git show -s --pretty=%s").trim()

        app                     = ""
    }


    stages {

        stage("Unit Testing") {
            
            steps {
                echo 'Unit testing'
            }
        }

        stage('Deployment') {
            parallel {
                stage('Staging') {  
                   
                    steps {
                        echo 'staging...'
                    }
                }

                stage('Demo') {  
                    
                    steps {
                        echo 'demo...'
                    }
                }

                stage('Production') {
                    
                    steps {
                        echo 'production...'
                    }
                }

            }
        }
    }

    post {
        success {
            slackSend color: "#03CC00", message: "*Build Succeeded (${env.BUILD_NUMBER})*\n Job: ${env.JOB_NAME}\n Commit: ${env.GIT_MESSAGE}\n Author: ${env.GIT_COMMITTER_NAME}\n <${env.RUN_DISPLAY_URL}|Open Jenkins Log>"
        }
        failure {
            slackSend color: "#FF0000", message: "*Build Failed (${env.BUILD_NUMBER})*\n Job: ${env.JOB_NAME}\n Commit: ${env.GIT_MESSAGE}\n Author: ${env.GIT_COMMITTER_NAME}\n <${env.RUN_DISPLAY_URL}|Open Jenkins Log>"
        }
    }
}