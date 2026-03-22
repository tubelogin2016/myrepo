pipeline {
agent any

environment {
IMAGE_NAME = "myorgdocker1/myrepo:v1"
CONTAINER_NAME = "myrepo-app"
}

stages {
stage('Clone Source') {
steps {
git branch: 'main', url: 'https://github.com/tubelogin2016/myrepo.git'
}
}

stage('Build Docker Image') {
steps {
sh 'docker build -t $IMAGE_NAME .'
}
}

stage('Push Docker Image') {
steps {
sh 'docker login -u myorgdocker1 -p Kolkata$123'
sh 'docker push $IMAGE_NAME'
}
}

stage('Run Docker Container') {
steps {
sh 'docker rm -f $CONTAINER_NAME || true'
sh 'docker run -d --name $CONTAINER_NAME -p 8085:80 $IMAGE_NAME'
}
}
}
}
