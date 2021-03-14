pipeline {
    agent any

    stages {

        stage("Unit Testing") {
            options {
                timeout(time: 1, unit: "MINUTES")
            }
            steps {
                echo 'Unit testing'
            }
        }

        stage('Staging') {  
            options {
                timeout(time: 1, unit: "MINUTES")
            }  
            steps {
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
                        echo 'develop equals master branch...'
                    }
                }

                stage('Demo') {  
                    options {
                        timeout(time: 1, unit: "MINUTES")
                    }
                    when {
                        branch 'demo'
                    }
                    steps {
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
                echo 'cleaning up...'
            }
        }
           
    }

    
}