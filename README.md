# maven-web-app
===============================================================
Jenkins integrate with docker :  
prerequisite
---------------
1) launch two ec2 instances
2) first server like jenkins server, you installed java, git, jenkins and docker also .
3) sercond server like build server, you installed docker only .
    To connect jenkins server type docker info 
      you getting docker.sock error
4) when ever you build application your pipeline you getting error .
    docker deamon not runining so we need to change  permisons like /var/run/docker.sock
    * first create user  in jenkins server 
      sudo useradd -aG jenkins 
    * To restart docker 
      sudo service docker restart
    * docker info you get successfull information about docker that jenkins user 
 
  
    
