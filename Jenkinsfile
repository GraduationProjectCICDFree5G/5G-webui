pipeline {
   agent any
   environment {
    DOCKERHUB_CREDENTIALS=credentials('Dockerhub')
   }

   stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Login to DockerHub') {

            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        }
        stage('build and push webui image') {
            steps {
                sh(script: """
                    docker images
                    make base
                    cd webui
                    docker build -t 5ggraduationproject/webui .
                    docker push 5ggraduationproject/webui
                    cd ..
                """)
                }
        }
    }
    
