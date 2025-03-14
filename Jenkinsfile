pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building node application is starting'
            }
        }
        stage('Deploy to dev') {
            steps {
                echo 'Deployment to DEV has started'
            }
        }
        stage('Tests on dev') {
            steps {
                echo 'Testing on DEV has started'
            }
        }

        //Fake staging environment
        stage('Deploy to STG') {
            steps {
                echo 'Deployment to STG has started'
            }
        }
        stage('Tests on STG') {
            steps {
                echo 'Testing on STG has started'
            }
        }

        //Fake production environment
        stage('Deploy to PRD') {
            steps {
                echo 'Deployment to PRD has started'
            }
        }
        stage('Tests on PRD') {
            steps {
                echo 'Testing on PRD has started'
            }
        }
    }
}
