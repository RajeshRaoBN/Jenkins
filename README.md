# Jenkins

This is the Jenkins Repo

First Course online is 

https://www.youtube.com/watch?v=WvcHQtyPcTs&ab_channel=DevOpsShack

Jenkins Full Course 2023 | Jenkins Tutorial For Beginners from DevOps Shack

Instructions: 

Create an AWS EC2 Instance using ubuntu. Go for a free tier 

Note: in the Security group create TCP with port 8080 exposed to all traffic from 0:0:0:0

Connect the EC2 and follow the instruction to install jenkins on the ubuntu EC2 instance https://www.jenkins.io/doc/book/installing/linux/

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

Install Java and check for version

sudo apt update
sudo apt install fontconfig openjdk-17-jre

java -version

openjdk version "17.0.8" 2023-07-18
OpenJDK Runtime Environment (build 17.0.8+7-Debian-1deb12u1)
OpenJDK 64-Bit Server VM (build 17.0.8+7-Debian-1deb12u1, mixed mode, sharing)

Start Jenkins
You can enable the Jenkins service to start at boot with the command:

sudo systemctl enable jenkins
You can start the Jenkins service with the command:

sudo systemctl start jenkins
You can check the status of the Jenkins service using the command:

sudo systemctl status jenkins
If everything has been set up correctly, you should see an output like this:

Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
Active: active (running) since Tue 2018-11-13 16:19:01 +03; 4min 57s ago
If you have a firewall installed, you must add Jenkins as an exception. You must change YOURPORT in the script below to the port you want to use. Port 8080 is the most common.

YOURPORT=8080
PERM="--permanent"
SERV="$PERM --service=jenkins"

firewall-cmd $PERM --new-service=jenkins
firewall-cmd $SERV --set-short="Jenkins ports"
firewall-cmd $SERV --set-description="Jenkins port exceptions"
firewall-cmd $SERV --add-port=$YOURPORT/tcp
firewall-cmd $PERM --add-service=jenkins
firewall-cmd --zone=public --add-service=http --permanent
firewall-cmd --reload


