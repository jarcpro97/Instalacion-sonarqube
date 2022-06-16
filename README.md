# Instalacion-sonarqube

Imagen docker windows

1. Instalar docker desktop
2. Abrir powershell
3. ejecutar docker run -d --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:lts-community 
