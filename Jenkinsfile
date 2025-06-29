pipeline {
    agent none

    environment {
        DEPLOY_IMAGE_NAME = 'prajol/zola-blog'
        DEPLOY_IMAGE_TAG = 'latest'
        CONTAINER_NAME = 'prajol-zola-blog'
    }
    stages {
        stage('Checkout') {
            agent any
            steps {
                checkout scm
            }
        }

        stage('Build Static Assets') {
            agent {
                docker {
                    image 'ghcr.io/getzola/zola:v0.20.0'
                    reuseNode true
                    args '--entrypoint=sh -u root:root'
                }
            }

            steps {
                echo 'Building Static assets inside container...'
                sh 'zola build --output-dir public'
            }
            post {
                success {
                    echo 'Stashing compiled assets...'
                    stash name: 'assets', includes: 'public/**'
                }
            }
        }

        stage('Deploy') {
            agent any
            steps {
                echo 'Preparing to build deployment image...'
                unstash 'assets'
                echo "Building the final deployment image (${env.DEPLOY_IMAGE_NAME}:${env.DEPLOY_IMAGE_TAG})..."
                sh "docker build -t ${env.DEPLOY_IMAGE_NAME}:${env.DEPLOY_IMAGE_TAG} -f Dockerfile.deploy ."

                echo 'Deploying the application...'
                echo 'Stopping and removing old container if it exists...'
                sh "docker stop ${env.CONTAINER_NAME} || true"
                sh "docker rm ${env.CONTAINER_NAME} || true"

                echo 'Starting new container...'
                sh "docker run -d --name ${env.CONTAINER_NAME} -p 8083:80 ${env.DEPLOY_IMAGE_NAME}:${env.DEPLOY_IMAGE_TAG}"
            }

            post {
                always {
                    script {
                        echo '--- Entering Post-Build Actions ---'

                        echo "Unstashing artifact 'assets'..."
                        try {
                            unstash 'assets'
                            echo 'Artifact unstashed successfully.'

                            echo 'Archiving artifact: static assets'
                            archiveArtifacts artifacts: 'static assets', fingerprint: true
                            echo 'Artifact archived successfully.'
                        }
                    catch (err) {
                            echo "Error during unstash or archive: ${err}"
                            currentBuild.result = 'FAILURE'
                    }

                        echo '--- Exiting Post-Build Actions ---'
                    }
                }
            }
        }
    }
}
