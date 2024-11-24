*************************************** Docker local repository configuration *****************************

> Installation Steps:

1. Docker Installation:

#sudo apt update

#sudo apt install apt-transport-https ca-certificates curl software-properties-common

#curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

#echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#sudo apt update

#apt-cache policy docker-ce

#sudo apt install docker-ce

If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group

#sudo usermod -aG docker ubuntu




2. To apply the new group membership, log out of the server and back in, or type the following:

#su – ubuntu

#groups

#docker –version


3. Docker compose Installation:

#mkdir -p ~/.docker/cli-plugins/

#curl -SL https://github.com/docker/compose/releases/download/v/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose

#chmod +x ~/.docker/cli-plugins/docker-compose

#docker compose version


4. Docker compose file:

Created docker-compose file under /data partition.

Note: Certs, reg-data, docker-compose directories are created under /data partition and same have been used in yaml file.

Assuming you have valid ssl certificate or you can create self-signed certificate.

To run docker compose file:

#docker compose up -d


5. Pulling the nginx image from docker hub:

#docker pull nginx

Tag and Push the nginx image to private docker repository

#docker tag nginx:latest repo.example.com/example-nginx

#docker push repo.example.com/example-nginx

       

6. Now you can pull this nginx image by using below command from other server without connecting to docker Hub. It will pull image from your private docker reposiotry.

#docker pull repo.example.com/example-nginx

Note: Please make sure repo.example.com is rechable from other server.
