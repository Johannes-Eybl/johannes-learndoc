#ÜK
#telematik

# IP-Adressen

- In einem (lokalen) Netzwerk muss jede Adresse eindeutig sein.
- Adressen werden genutzt, damit Geräte im Netz unter einander kommunizieren können.
- Adressen werden entweder dynamisch zugewiesen oder sie müssen selber konfiguriert werden.

## Begriffe

IP-Adresse → Adressierung einer Netzwerk-Komponente

Netzmaske → Ergibt die Grösse des eigenen Netzwerks

Gateway → Nächste Station, um Netz zu verlassen (zb. Internet)

DNS → Namensauflösung zu IP-Adresse

zb. [www.google.com](http://www.google.com) → 157.161.155.144

DHCP → Automatische Verteilung von Adressen

# IPv4

- Jede IPv4-Adresse hat vier Zahlen, die zwischen 0 und 255 liegen
    - Beispiel: 192.168.1.25
- Technisch gesehen ist es eine 32-Stellige Binärzahl
- Private IPs haben folgende Zahlen am Anfang:
    - 192.168.x.x
    - 172.16.x.x bis 172.31.x.x
    - 10.x.x.x
    - 169.254.x.x