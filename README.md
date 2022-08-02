# Instalacion-sonarqube

Imagen docker windows

1. Instalar docker desktop
2. Abrir powershell
3. ejecutar docker run -d --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:lts-community 

Sonarqube en docker-compose

sudo sysctl -w vm.max_map_count=262144
mkdir sonar
sudo touch docker-compose.yml
sudo docker-compose up -d

ver logs
sudo docker-compose logs -f sonarqube
