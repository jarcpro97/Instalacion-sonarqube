# Instalacion-sonarqube

Imagen docker windows

1. Instalar docker desktop
2. Abrir powershell
3. ejecutar docker run -d --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:lts-community 

Sonarqube en Docker con docker-compose

cd /opt
mkdir sonar
sudo touch docker-compose.yml
sudo nano docker-compose.yml 
sudo docker-compose up -d

ver logs
sudo docker-compose logs -f sonarqube
sudo docker logs sonar_sonarqube_1
  
  
  Referencias:
  https://awstip.com/installing-sonarqube-on-aws-ec2-instance-and-integrating-it-with-aws-codepipeline-abec99416ba4
  https://docs.sonarqube.org/9.9/