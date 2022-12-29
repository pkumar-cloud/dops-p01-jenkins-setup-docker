# Use this repo if folloiwng RPT01 approach. 
## jenkins-setup-docker

  1. git clone this repo & execute the ./docker-setup.sh on master and slave nodes.
  2. Install Java and Maven on slave node.
      sudo yum install java-1.8.0-openjdk java-1.8.0-openjdk-devel -y **devel package is used for maven
      sudo yum install maven 
  3. docker-compose up -d on Master node. // docker-compose up -d --scale jenkins=3
  4. Configure Master via UI.

## Configure Jenkins Cluster
  
  1. Create the Jenkins master node
  2. Create the slave node.
  3. Execute ssh-keygen -t rsa -b 4096 -m PEM command in the master node. //Only allows respective PEM key to connect to slave.
  4. Copy the content of id_rsa.pub file and paste it in the authorized_key file of slave node.
  5. Copy the content of the id_rsa file from master node in step-7.
  6. Got to the Jenkins UI > Manage Jenkins -> Manage Credentials.
  7. Create a new Credentials of Kind "SSH Username and private Key". Add anyname as ID, username:ec2-user/ubuntu/centos etc..
  8. Then go the Manage Jenkins -> Manage Node. Create a new node.
      * Number of executers
      * Remote root directory: /home/ec2-user/jenkins - on slave which folder to use for code checkout. // Create folder on slave node. 
      * Labels: define a label
      * Launch method: "Launch agents via SSH", Configure: (Host:Slave IP/Name), Credentials(Select created above), Host key verification strategy ("Non verifying verification strategy")
      * Launch Agent. 


