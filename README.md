# Jenkins-Demo-Pipeline

<br />

Install Jenkins, Configure Jenkins and expose to outside world.

## AWS EC2 Instance

<br />

- Go to AWS Console
- Instances(running)
- Launch instances

## Install Jenkins

<br />

Pre-Requisites:
 - Java (JDK)

## Run the below commands to install Java and Jenkins

<br />

Install Java

```
sudo apt update
sudo apt install openjdk-11-jre
```

Verify Java is Installed

```
java --version
```
Now, you can proceed with installing Jenkins

```
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
<br />

### By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

Add inbound traffic rules as shown in the image:

<br />

![f2](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/7ba903d6-868e-4181-80bc-3b7ed65c47df)

<br />

## Login to Jenkins using the below URL:

<br />

http://<ec2-instance-public-ip-address>:8080    [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

After you login to Jenkins, 
      - Run the command to copy the Jenkins Admin Password - `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`
      - Enter the Administrator password

<br />

![f3](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/2c0af7a8-7da8-42e6-9dd2-faedc91ac909)

<br />

## Click on Install suggested plugins

<br />

![f4](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/83fd70c6-4cd6-4805-81b5-4190f85192df)

<br />

Wait for the Jenkins to Install suggested plugins.

<br />

![f5](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/d09695ed-6127-493d-8469-5b225c14d5ee)

<br />

Create First Admin User or Skip the step.

<br />

![f6](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/a66b5a31-ccc9-484b-a48c-8c0b1a175aee)

<br />

Jenkins Installation is Successful. You can now starting using the Jenkins 

<br />

![f7](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/dc774b22-b7b6-4810-b7b6-37af11e3861c)

<br />

## Install the Docker Pipeline plugin in Jenkins:

<br />

   - Log in to Jenkins.
   - Go to Manage Jenkins > Manage Plugins.
   - In the Available tab, search for "Docker Pipeline".
   - Select the plugin and click the Install button.
   - Restart Jenkins after the plugin is installed.

<br />

![f9](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/05c1a5a5-0e4a-4266-a4ef-cde9afe9070f)

<br />

Wait for the Jenkins to be restarted.

<br />

## Docker Slave Configuration

<br />

Run the below command to Install Docker

```
sudo apt update
sudo apt install docker.io
```
 
### Grant Jenkins user and Ubuntu user permission to docker deamon.

<br />

```
sudo su - 
usermod -aG docker jenkins
usermod -aG docker ubuntu
systemctl restart docker
```
You can run the below command to check if docker is up and running:

```
docker run hello-world
```

<br />

![f8](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/d244a404-59c0-4ff0-9fd5-d6089a00ed04)

<br />

Once you are done with the above steps, it is better to restart Jenkins.

```
http://<ec2-instance-public-ip>:8080/restart
```

The docker agent configuration is now successful.
