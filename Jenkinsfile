node ('') {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
    
    stage('Build image') {
        app = docker.build("stevenzhou2006/front-end")
    }
    
    stage('Destroy running one') {
            sh "docker-compose -f /home/cloud/microservices-demo/deploy/docker-compose/docker-compose.yml down -v"
    } 
    
    stage('Deploy latest') {
            sh "docker-compose -f /home/cloud/microservices-demo/deploy/docker-compose/docker-compose.yml up -d"
    }     
    /*
    stage('Push image') {
        docker.withRegistry('http://localhost', '') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
    stage('Deploy') {
        sshagent(credentials: ["91c21a26-fcba-4c0e-824e-e4d0fd12c067"]) {
            sh "ssh steven@23.97.67.158 \"echo ${env.BUILD_ID}\""
        }        
    }
    
    stage('Deploy') {
         sshagent(credentials: ["91c21a26-fcba-4c0e-824e-e4d0fd12c067"]) {
            sh "ssh steven@23.97.67.158 \"echo ${env.BUILD_ID}\""
        }        
    }
    */
}
