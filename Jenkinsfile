pipeline {
    agent { label "ip-172-31-92-113" }
    stages{
        stage("Clone Code"){
            steps{
                git url: "https://github.com/CloudLinuxDeveloper/node-cicd-.git", branch: "master"
            }
        }
        stage("Build and Test"){
            steps{
                sh "docker build . -t node-cicd-"
            }
        }
        //stage("Push to Docker Hub"){
            //steps{
               // withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                //sh "docker tag nodeapp ${env.dockerHubUser}/node-cicd-:latest"
                //sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                //sh "docker push ${env.dockerHubUser}/node-cicd-:latest"
                //}
            //}
        //}
        stage("Deploy"){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
