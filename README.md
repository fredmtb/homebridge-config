

1) Grundlegende Updates und Software installieren:

	sudo apt-get update
	sudo apt-get dist-upgrade
	sudo apt-get remove ntpd
	sudo apt-get install openntpd git make libavahi-compat-libdnssd-dev
	sudo systemctl enable openntpd.service
	sudo systemctl start openntpd.service


2) Node installieren

	wget https://nodejs.org/dist/v4.0.0/node-v4.0.0-linux-armv7l.tar.gz 
	tar -xvf node-v4.0.0-linux-armv7l.tar.gz 
	cd node-v4.0.0-linux-armv7l
	sudo cp -R * /usr/local/


3) Homebridge installieren

	git clone https://github.com/fredmtb/homebridge-config.git
	cd homebridge-config
	sudo npm install -g homebridge homebridge-fhem
	sh install.sh
