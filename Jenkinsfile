pipeline {
    agent any

    stages {
        stage('One') {
            steps {
                echo 'Building for the Oswagos................'
            }
        }
        
        stage('Two') {
            steps {
                input('Do you want to proceed?')
            }
        }
        
        stage('Three') {
            when {
                not {
                    branch 'main'
                }
            }
            steps {
                echo 'Hello.......'
            }
        }
        
        stage('Four') {
            parallel {
                stage('Unit Test') {
                    steps {
                        echo 'Running the Unit Test......'
                    }
                }
                stage('Integration test') {
                    agent {
                        docker {
                            image 'ubuntu'  // Note: use lowercase 'ubuntu' for the official image
                            reuseNode true  // This ensures the container shares the workspace with the main node
                        }
                    }
                    steps {
                        echo 'Running the Integration test........'
                    }
                }
            }
        }
    }
}
