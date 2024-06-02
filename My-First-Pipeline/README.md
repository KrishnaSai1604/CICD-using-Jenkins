# My-First-Pipeline
 - Created a Jenkins pipeline with Docker as a Agent.
 - This is a simple pipeline to verify Docker agent configuration is working as expected.

# Steps:
# AWS EC2 Instance
  - Go to AWS Console
  - Launch instances
# Install Jenkins
 - Pre-Requisites:

Java (JDK)

# Run the below commands to install Java and Jenkins
 - Install Java
   - sudo apt update
   - sudo apt install openjdk-11-jre
- Verify Java is Installed
  - java -version
- Now, you can proceed with installing Jenkins
  - curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
  - sudo apt-get update
  - sudo apt-get install jenkins
- **Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules
# Login to Jenkins using the below URL
 - http://:8080 [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]
 - After you login to Jenkins, - Run the command to copy the Jenkins Admin Password - sudo cat /var/lib/jenkins/secrets/initialAdminPassword - Enter the Administrator password
# Install the Docker Pipeline plugin in Jenkins:
 - Log in to Jenkins.
 - Go to Manage Jenkins > Manage Plugins.
 - In the Available tab, search for "Docker Pipeline".
 - Select the plugin and click the Install button.
 - Restart Jenkins after the plugin is installed.
# Docker agent Configuration
 - Run the below command to Install Docker in launched server
   - sudo apt update
   - sudo apt install docker.io
# Grant Jenkins user and Ubuntu user permission to docker deamon.
 - usermod -aG docker jenkins
 - usermod -aG docker ubuntu
 - systemctl restart docker

 - Once you are done with the above steps, it is better to restart Jenkins again
  - http://<ec2-instance-public-ip>:8080/restart (type this in browser to restart jenkins again)
- The docker agent configuration is now successful.

