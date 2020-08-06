node
{ 
    stage("gitcheckout") 
    {
        git 'https://github.com/12ashok/mithun-maven-project.git'
        // jenkins takes code from github //
    }
    stage("mavenbuild")
    {
        def mavenHome= tool name: "maven",type: "maven"
        sh "${mavenHome}/bin/mvn clean package "
    }
    stage("building docker image")
    {
        sh 'docker build -t 12ashok/app:1 . '
        //Build a docker image. after building image we need to push dockerhub or privatehub//
    }
    stage("dockerlogin")
    {
        sh 'docker login -u 12ashok -p ashok1234@'
        //login to dockerHub //
    }
    stage("push the docker image")
    {
        sh 'docker push 12ashok/app:1' 
        // push into our dockerhub //
    }
     stage("deploy to Buildserver ")
    {
        // To deploy application to Build server //
        sshagent(['docker']) 
        {
            sh 'ssh -o StrictHostKeyChecking=no ec2-user@172.31.13.198 docker rm -f mv1 || true '
            // why putting above command the conatiner there to delete that conatiner //
            sh 'ssh ec2-user@172.31.13.198 docker rm -f $(docker ps -aq) || true '
             // To run docker container below command //
            sh 'ssh ec2-user@172.31.13.198 docker run -d -p 8989:8080 --name mv1 12ashok/app:1 '
        }
    }
}
