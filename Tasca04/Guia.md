# CONFIGURACIÓ MAQUINA  
Per configurar la màquina virtual he posat 4096MB de RAM  

En el primer Adaptador he posat xarxa NAT  

I en el segon adaptador he posat Adaptador de només l’amfitrió  

Entrerem al arxiu de /etc/netplan/50-cloud-init-yaml amb sudo nano y posarem aquesta configuració  

Ara configurarem el domini, per fer això obrirem el arxiu de /etc/hosts amb sudo nano, dintre del arxiu cambiarem el domini que està després del 127.0.1.1  

# INSTAL.LACIÓ I CONFIGURACIÓ D’OPENLDAP  

Per instal·lar OpenLDAP, primer ens hem de posar com a root amb sudo su, i després l’hem d’instal·lar amb la comanda apt install slapd ldap-utils -y.  

Un cop hem posat això, ens sortirà aquesta finestra, on haurem d’introduir la contrasenya.  

Un cop instal·lat, comprovem que el servei està funcionant amb la comanda systemctl status slapd.  

Per configurar el domini, entrarem com a root amb la comanda sudo su i després executarem la comanda dpkg-reconfigure slapd.  

I per comprovar-ho, executarem la comanda slapcat mentre estem com a root.  

