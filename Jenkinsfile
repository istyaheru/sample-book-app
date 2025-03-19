pipeline {
    agent any
    triggers{ pollSCM('*/1 * * * *') }
    

    stages {
        stage('Build') {
            steps {
                echo 'Building node application is starting'
                sh "ls"
                sh "npm install"
                //sh "npm test"
            }
        }
        stage('Deploy to dev') {
            steps {
                script{
                    deploy("DEV", 1010)
                }
            }
        }
        stage('Tests on dev') {
            steps {
                script{
                    test("BOOKS", "DEV")
                }
            }
        }

        //Fake staging environment
        stage('Deploy to STG') {
            steps {
                script{
                    deploy("STG", 2020)
                }
            }
        }
        stage('Tests on STG') {
            steps {
                script{
                    test("BOOKS", "STG")
                }
            }
        }

        //Fake production environment
        stage('Deploy to PRD') {
            steps {
                script{
                    deploy("PRD", 3030)
                }
            }
        }
        stage('Tests on PRD') {
            steps {
                script{
                    test("BOOKS", "PRD")
                }
            }
        }
    }
}

def deploy(String env, int port){
    echo "Deployment to ${env} has started"
    git branch: 'main', poll: false, url: 'https://github.com/istyaheru/sample-book-app.git'
    //sh "pm2 start -h \"books-${env}\"""
    sh "pm2 delete \"books-${env}\" || exit 0"
    sh "pm2 start -h \"books-${env}\" index.js -- ${port}"
}

def test(String test_set, String env){
    echo "Testing ${test_set} on ${env} has started"
    git branch: 'main', poll: false, url: 'https://github.com/istyaheru/api-automation.git'
    sh "npm install"
    sh "npm run ${test_set} ${test_set}_${env}"
}
