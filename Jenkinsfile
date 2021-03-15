pipeline {
    agent any

    stages {

        stage("Unit Testing") {
            options {
                timeout(time: 1, unit: "MINUTES")
            }
            steps {
                sh 'sleep 30s'
                echo 'Unit testing'
            }
            
        }

        stage('Staging') {  
            options {
                timeout(time: 1, unit: "MINUTES")
            }  
            steps {
                sh 'sleep 30s'
                echo 'staging...'
            }
        }

        stage('Deployment') {
            parallel {
                stage('Staging') {  
                    options {
                        timeout(time: 1, unit: "MINUTES")
                    }
                    when {
                        branch 'master'
                    }
                    steps {
                        sh 'sleep 30s'
                        echo 'develop equals master branch...'
                    }
                }

                stage('Demo') {  
                    options {
                        timeout(time: 2, unit: "MINUTES")
                    }
                    when {
                        branch 'demo'
                    }
                    steps {
                        sh 'sleep 30s'
                        echo 'demo view...'
                    }
                }

                stage('Production') {
                    options {
                        timeout(time: 1, unit: "MINUTES")
                    }
                    when {
                        branch 'production'
                    }
                    steps {
                        sh 'sleep 30s'
                        echo 'production...'
                    }
                }

            }
        }

        stage('Cleanup') {  
            options {
                timeout(time: 2, unit: "MINUTES")
            }
            steps {
                sh 'sleep 30s'
                echo 'cleaning up...'
            }
        }

        post {
            always {
                cleanWs()
            }
        }
           
    }

    
}