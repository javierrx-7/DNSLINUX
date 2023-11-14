# En esta práctica tendrás que configurar el servidor de DNS, en Linux 
## Utiliza una máquina virtual Ubuntu Server LTS

- UbuntuServerLTS

## Instala bind9 con apt

- sudo apt install bind9

## Configura el DNS igual que en docker
- cd /etc/bind/
- ls -l

- sudo nano named.config

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";

- sudo nano.conf.options

options {
	directory "/var/cache/bind";

	forwarders {
	 	8.8.8.8;
		1.1.1.1;
	 };
	 forward only;

	listen-on { any; };
	listen-on-v6 { any; };

	allow-query {
		any;
	};
};

- configuramos la red en 

;
; BIND data file for local loopback interface
;
    $TTL	604800
@	IN	SOA	localhost. root.localhost. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
@	IN	A	127.0.0.1
@	IN	AAAA	::1

- sudo service bind9 status
- Por ultimo ponemos cd nano /etc/netplan/01-netcfg.yaml
- Ponemos la ip del servidor local en addresses.
- sudo netplan apply, para aplicarlo.


## Comprueba (en el propioservidor) con el comando 'dig' que el servidor funciona
- dig (nombre del servidor)

        dig @172.16.0.1 www.ejercicioDNS.int

- dig SOA (nombre del servidor)

