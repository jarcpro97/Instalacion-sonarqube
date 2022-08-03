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

docker-compose.yml
version: '2'

services:
  sonarqube:
    image: lts-community
    ports:
      - '9000:9000'
    networks:
      - sonarnet
    environment:
      - sonar.jdbc.username=sonar
      - sonar.jdbc.password=sonar
      - sonar.jdbc.url=jdbc:postgresql://db:5432/sonar
    volumes:
      - sonarqube_conf:/opt/sonarqube/conf
      - sonarqube_data:/opt/sonarqube/data
      - sonarqube_extensions:/opt/sonarqube/extensions
    ulimits:
      nofile:
       soft: 65536
       hard: 65536
  db:
    image: postgres
    networks:
      - sonarnet
    environment:
      - POSTGRES_USER=sonar
      - POSTGRES_PASSWORD=sonar
    volumes:
      - postgresql:/var/lib/postgresql
      # This needs explicit mapping due to https://github.com/docker-library/postgres/blob/4e48e3228a30763913ece952c611e5e9b95c8759/Dockerfile.template#L52
      - postgresql_data:/var/lib/postgresql/data

networks:
  sonarnet:
    driver: bridge

volumes:
  sonarqube_conf:
  sonarqube_data:
  sonarqube_extensions:
  postgresql:
  postgresql_data:
  
  
  Referencias:
  https://awstip.com/installing-sonarqube-on-aws-ec2-instance-and-integrating-it-with-aws-codepipeline-abec99416ba4
