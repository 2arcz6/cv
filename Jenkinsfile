pipeline {
    agent any

    stages {

        stage("Unit Testing") {
            
            steps {
                echo 'Unit testing'
            }
        }

        stage('Staging') {  
            
            steps {
                echo 'staging...'
            }
        }

        stage('Deployment') {
            parallel {
                stage('Staging') {  
                    when {
                        branch 'master'
                    }
                    steps {
                        echo 'developing ...'
                    }
                }

                stage('Demo') {  
                    
                    when {
                        branch 'demo'
                    }
                    steps {
                        echo 'demo test view...'
                    }
                }

                stage('Production') {
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
            
            steps {
                echo 'cleaning up...'
            }
        }
           
    }

    
}