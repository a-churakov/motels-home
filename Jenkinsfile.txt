pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                }
            }
            steps {
                sh 'python -m py_compile com.training.spark/constants.py com.training.spark/MotelsHomeRecommendation_empty.py'
                stash(name: 'compiled-results', includes: 'com.training.spark/*.py*')
            }
        }
    }
}