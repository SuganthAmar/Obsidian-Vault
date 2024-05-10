![[Pasted image 20240319215139.png]]

This process is done by multiple developer multiple times 
But the problem is:
![[Pasted image 20240319215241.png]]

![[Pasted image 20240319215336.png]]

![[Pasted image 20240319215408.png]]

![[Pasted image 20240319215636.png]]

# Jenkins Installation on Debian based linux

```bash
sudo apt update 
sudo apt install openjdk-11-jdk -y
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
```

After this the Initial Password can be found at : /var/lib/jenkins/secrets/initialAdminPassword

## Jenkins will run on a Specific user 
that user can be found at :=> ` /var/lib/jenkins

id jenkins => will show the user id of the machine

## Run Jenkins

use the public ip or the dns to run on port 8080

Select the plugins for the integration process
Login with user or create a new user 

# Jobs in Jenkins
## 1) Freestyle
## 2) Pipeline

## Jobs is defined as the work load that the machine operates on 

![[Pasted image 20240320103644.png]]

To start with jenkins we need the plugins and the tool itself

## Jdk tools location is `/usr/lib/jvm/"java jdk version"`


# Flow of Continuous Integration

![[Pasted image 20240320140908.png]]

SonarQube is a Code Analysis platform
NexusOSS is a Storage medium where the different versions of artifacts will be stored 

## Steps for Continuous Integration
![[Pasted image 20240320141615.png]]

