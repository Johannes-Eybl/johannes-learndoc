# Übersicht Container
`sudo docker ps -a`
# Container Starten / Stoppen
`sudo docker start CONTAINERNAME`
`sudo docker stop CONTAINERNAME`
# Konsolen-Output von Docker in Terminal anzeigen
`sudo docker logs -f CONTAINERNAME`
# In Container einloggen
`sudo docker exec -it CONTAINERNAME sh`
alternativ
`sudo docker exec -it CONTAINERNAME /bin/sh`
# Container löschen
`docker rm CONTAINERNAME`
# Logs|Output von Container abfragen
`docker logs CONTAINERNAME`
Mit der `-f`-Option ("follow") kann man live-output enabeln:
`docker logs -f CONTAINERNAME`
