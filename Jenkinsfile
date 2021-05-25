pipeline {
    agent {
      docker {
        image 'python'
      }
    }
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                }
            }
            steps {
                sh 'python -m py_compile venv/com.training.spark/constants.py venv/com.training.spark/MotelsHomeRecommendation_empty.py'
                stash(name: 'compiled-results', includes: 'venv/com.training.spark/*.py*')
            }
        }
    }
}