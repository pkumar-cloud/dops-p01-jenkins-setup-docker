# jenkins-setup-docker

  1. First execute the docker-setup.sh on master and slave nodes.
  2. Install Java and Maven on slave node.
      yum install java-1.8.0-openjdk java-1.8.0-openjdk-devel -y **devel package is used for maven
      
  3. docker-compose up -d on Master node.
  4. Configure Master via UI.

# Configure Jenkins Cluster
  
  1. Create the Jenkins master node
  2. Create the slave node.
  3. Execute ssh-keygen -t rsa -b 4096 -m PEM command in the master node.
  4. Copy the content of id_rsa.pub file and paste it in the authorized_key file of slave node.
  5. Copy the content of the id_rsa file from master node.
  6. Got to the Jenkins UI > Manage Jenkins -> Manage Credentials.
  7. Create a new Credentials of Kind "SSH Username and private Key"
  8. Then go the Manage Jenkins -> Manage Node. Create a new node.
      * <b> Number of executers
      * <b> Remote root directory: /home/jenkins - on slave which folder to use for code checkout.
      Labels: define a label
      Launch method: Launch agents via SSH (Host:Slave IP/Name)


