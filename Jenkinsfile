node {
    def app

    stage('Clone repository') {
        /* repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* To builds the dockerimage */
        //update your ECR registry URI
       //me  app = docker.build("843554782143.dkr.ecr.ap-south-1.amazonaws.com/ischool-ui")
       sh 'sudo docker build -t 993397683587.dkr.ecr.ap-south-1.amazonaws.com/test:build-v${BUILD_NUMBER} .'
    }


    stage('Push image') {
        /* Finally, we'll push the image */
        //docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
        // update your ECR registry URI and jenkins crendential paramater
        //docker.withRegistry('https://843554782143.dkr.ecr.ap-south-1.amazonaws.com/ischool-ui', 'ecr:ap-south-1:aws-ecr-credentials')    {
            //app.push("${env.BUILD_NUMBER}")
        //    app.push("latest")
        //}
        sh 'sudo docker push 993397683587.dkr.ecr.ap-south-1.amazonaws.com/test:build-v${BUILD_NUMBER}'
    }


    stage('Deploy to k8s') {
        /* To builds the dockerimage */
        //update your ECR registry URI
       //me  app = docker.build("843554782143.dkr.ecr.ap-south-1.amazonaws.com/ischool-ui")
       sh 'sudo sed -i 's/latest/build-v${BUILD_NUMBER}/g' deployment.yaml && kubectl apply -f deployment.yml'
    }
}
