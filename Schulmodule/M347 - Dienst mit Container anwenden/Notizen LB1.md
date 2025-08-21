# Docker-Image
- [ ] Ein Image erstellen
- [ ] Das Image pushen
- [ ] Eine Anleitung schreiben, wie das Image installiert werden kann
	- [ ] git clone
	- [ ] cd uebungsprojekt
	- [ ] docker-compose -f pfad/zum/file up -d

# Git-Accesstoken



## Befehle für Lehrer

git clone https://git.gibb.ch/jey149014/m347-uebungsprojekt.git

cd m347-uebungsprojekt/

docker build -t test:v1 .

docker run -d -p 5000:5000 --name my-container test:v1
