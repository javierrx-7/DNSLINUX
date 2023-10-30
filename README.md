# En esta práctica tendrás que configurar el servidor de DNS, en Linux 
## Utiliza una máquina virtual Ubuntu Server LTS

- UbuntuServerLTS

## Instala bind9 con apt

- sudo apt install bind9

## Configura el DNS igual que en docker
- cd /etc/bind/
- ls -l
- sudo nano named.config
- sudo nano.conf.options
- configuramos la red en 
- forwarders {
    8.8.8.8
    8.8.4.4
};
- y si queremos usando acl (nombre para las anuladas) {192.158.0.22}; encima de todo.
- Y justo debajo de las ips ponemos blackhole {
    (nombre de los anulados);
};
- hacemos control+o y despues control+x
- sudo service bind9 status
- Por ultimo ponemos cd nano /etc/netplan/01-netcfg.yaml
- Ponemos la ip del servidor local en addresses.
- sudo netplan apply, para aplicarlo.


## Comprueba (en el propioservidor) con el comando 'dig' que el servidor funciona
- dig (nombre del servidor)
- dig SOA (nombre del servidor)

