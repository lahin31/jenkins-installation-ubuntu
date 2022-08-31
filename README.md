# Jenkins Installation Process inside ubuntu

## Without Docker

From https://pkg.jenkins.io/debian/

- `sudo apt update` (update your system)
- `curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \
    /usr/share/keyrings/jenkins-keyring.asc > /dev/null`
- `echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null`
- `sudo apt-get update`
- `sudo apt-get install fontconfig openjdk-11-jre` (installing fontconfig and java sdk)
- `java -version` (checking java version)
- `sudo apt-get install jenkins` (installing jenkins)
- `sudo systemctl enable jenkins` (enabling jenkins)
- `sudo systemctl start jenkins` (starting jenkins)
- `sudo systemctl status jenkins` (checking jenkins status)

## With Docker

- `docker` (check docker is installed or not)
- `sudo apt install docker.io` (if not type this)
- `sudo docker pull jenkins/jenkins` (pulling jenkins)
- `sudo docker run -d -p 8080:8080 docker.io/jenkins/jenkins:latest`
- `sudo docker ps`
- `sudo systemctl status jenkins` (most probably you will see status is enable)
- `sudo chmod 666 /var/run/docker.sock`
- `docker exec {{container_id}} cat var/jenkins_home/secrets/initialAdminPassword` (get the password)
