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
                script{
                    deploy("DEV")
                }
            }
        }
        stage('Tests on dev') {
            steps {
                script{
                    test("DEV")
                }
            }
        }

        //Fake staging environment
        stage('Deploy to STG') {
            steps {
                script{
                    deploy("STG")
                }
            }
        }
        stage('Tests on STG') {
            steps {
                script{
                    test("STG")
                }
            }
        }

        //Fake production environment
        stage('Deploy to PRD') {
            steps {
                script{
                    deploy("PRD")
                }
            }
        }
        stage('Tests on PRD') {
            steps {
                script{
                    test("PRD")
                }
            }
        }
    }
}

def deploy(String env){
    echo "Deployment to ${env} has started"
}

def test(String env){
    echo "Testing on ${env} has started"
}
