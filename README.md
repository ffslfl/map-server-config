# Server config files hopglass map-server mit Prometheus und Grafana

## Installation

Die Datei install.sh enthält eine Schritt für Schritt Anleitung nach welcher die hopglass-map installiert ist. Als Betriebssystem wird debian etch angenommen. Die Verwendeten Komponenten sind:

- Webserver (Nginx, weil gzip-Komprimierung und reverse proxies damit einfacher sind)
- eine aktuelle Version von NodeJS (Version >4.3) (https://nodejs.org/en/download/package-manager/)
- Hopglass Server (https://github.com/plumpudding/hopglass-server)
- Hopglass Viewer (https://github.com/plumpudding/hopglass)
- Prometheus (http://prometheus.io)
- Grafana (http://grafana.org)

Die angepassten configs finden sich in den jeweiligen Unterverzeichnissen.


## Issues

Zur Zeit müssen ggf. die MAC Adressen der Supernodes nach einer Änderung händisch in den hopglass-server eingepflegt werden. Dies funktioniert über die Datei [hopglass-server/alias.json](hopglass-server/alias.json)



## Live

Zur Zeit ist diese map anzuschauen unter: https://karte.freifunk-flensburg.de/

# zusätzliche Anleitungen

https://libraries.io/github/hopglass/hopglass-server


##fastd
user der fastd ausführt muss netzwerkschnittstellen erstellen können(zb root)

fastd.conf muss nach /etc/fastd/_username_der_fastd_startet_/

secret in die fastd.conf eintragen

autostart mit systemd:

fastd@.service ---> /lib/systemd/system/fastd@.service

systemctl enable fastd@_username_der_fastd_startet_.service

##batman compat14 version 2013.4 erzwingen

dkms remove batman-adv/2013.4.0 --all

dkms --force install batman-adv/2013.4.0

batman-adv ---> /etc/modules

##webserver kopieren

/opt/hopglass/hopglass/build/* kopieren nach /var/www/html


##Prometheus und Grafana einrichten

#Prometheus und Grafana Webinterface einrichten:

Prometheus: http://localhost:9090

Grafana: http(s)://localhost:3000 oder  http(s)://localhost/grafana

http://localhost/grafana/login

default login: admin und Passwort: admin

https://localhost/grafana/datasources

https://localhost/grafana/datasources/new



Name: prometheus

Default (harken)

Type: Prometheus

Url: http://127.0.0.1:9090/

Http Auth: Basic Auth ( ) With Credentials ( )

klicke auf Test Connection

Test results
Success
Data source is working

Wenn alles Grün ist klicken wir auf ,,Save"






