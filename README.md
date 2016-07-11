Anleitung: Homebridge auf Raspberry Pi installieren

1)	Grundlegende Updates und Software installieren:
	sudo apt-get update
	sudo apt-get dist-upgrade
	sudo apt-get remove ntpd
	sudo apt-get install openntpd git make libavahi-compat-libdnssd-dev
	sudo systemctl enable openntpd.service
	sudo systemctl start openntpd.service

2)	Node installieren
	wget https://nodejs.org/dist/v4.0.0/node-v4.0.0-linux-armv7l.tar.gz 
	tar -xvf node-v4.0.0-linux-armv7l.tar.gz 
	cd node-v4.0.0-linux-armv7l
	sudo cp -R * /usr/local/

Um die Installation zu überprüfen  den Befehl node –v ausführen. In diesem Fall sollte die Ausgabe v-4.0.0 sein.

3)	Homebridge installieren
	git clone https://github.com/mattrayner/homebridge-config.git
	cd homebridge-config
	sudo npm install -g homebridge homebridge-fhem
	sh install.sh

4)	Config.json anpassen
Zuerst wird die Config.json-Datei gelöscht (sudo rm /home/pi/.homebridge/config.json) Anschließend wird eine neue Config.json-Datei erstellt (sudo nano /home/pi/.homebridge/config.json):

	{
	"bridge": {
	"name": "Homebridge",
	"username": "CC:22:3D:E3:CE:30",
	"port": 51826,
	"pin": "031-45-154"
	},
 
	"platforms": [
	{
	"platform": "FHEM",
	"name": "FHEM",
	"server": "127.0.0.1",
	"port": "8083",
	"filter": "room=Homekit",
	"auth": {"user": "FHEMUser", "pass": "FHEMPass"}
	}
	],
 
	"accessories": []
	}
