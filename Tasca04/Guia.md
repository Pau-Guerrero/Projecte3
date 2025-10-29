# CONFIGURACIÓ MAQUINA  
Per configurar la màquina virtual he posat 4096MB de RAM  

![](img/image1.png)

En el primer Adaptador he posat xarxa NAT  

![](img/image2.png)

I en el segon adaptador he posat Adaptador de només l’amfitrió  

![](img/image3.png)

Entrerem al arxiu de /etc/netplan/50-cloud-init-yaml amb sudo nano y posarem aquesta configuració  

![](img/image4.png)

Ara configurarem el domini, per fer això obrirem el arxiu de /etc/hosts amb sudo nano, dintre del arxiu cambiarem el domini que està després del 127.0.1.1  

![](img/image5.png)
![](img/image6.png)
![](img/image7.png)

# INSTAL.LACIÓ I CONFIGURACIÓ D’OPENLDAP  

Per instal·lar OpenLDAP, primer ens hem de posar com a root amb sudo su, i després l’hem d’instal·lar amb la comanda apt install slapd ldap-utils -y.  

![](img/image8.png)

Un cop hem posat això, ens sortirà aquesta finestra, on haurem d’introduir la contrasenya.  

![](img/image9.png)

Un cop instal·lat, comprovem que el servei està funcionant amb la comanda systemctl status slapd.  

![](img/image10.png)

Per configurar el domini, entrarem com a root amb la comanda sudo su i després executarem la comanda dpkg-reconfigure slapd.  

![](img/image11.png)
![](img/image12.png)

I per comprovar-ho, executarem la comanda slapcat mentre estem com a root.  

![](img/image13.png)

# LDAP UTILS
Primer obrirem el crearem i obrirem el archiu de OU_users.ldif amb sudo nano

![](img/image14.png)

Dintre del archiu escriurem aquest text

![](img/image15.png)

Aqui posarem la comanda de ldapadd -D "cn=admin,dc=innovatech09,dc=test" -W -f OU_users.ldif, aquesta ordre serveix per importar l’arxiu .ldif al directori LDAP utilitzant l’usuari administrador (cn=admin). El paràmetre -W fa que el sistema ens demani la contrasenya abans de continuar.

![](img/image16.png)

Aqui posarem la comanda de ldapsearch -xLLL -b "dc=innovatech09,dc=test" uid=* sn givenName mail, aquesta comanda fa una cerca dins del directori LDAP i mostra els camps uid, sn, givenName i mail dels usuaris existents per assegurar-nos que la informació s’ha carregat correctament.

![](img/image17.png)





# LDAP ACCOUNT MANAGER
Primer de tot instal.larem el paquet del gestor LDAP account manager

![](img/image18.png)

Si escrivim al navegador http://(la nostra IP)/lam, accedirem a la pàgina principal de LAM, on podrem iniciar sessió.

![](img/image19.png)

Pero abans de inicia sessió configurarem el LAM. Per això, anirem a la part superior dreta, on apareix una opció anomenada “Configuració de LAM”.
Un cop hi fem clic, s’obrirà un menú on haurem de seleccionar l’opció “Editar perfils del servidor”.

![](img/image20(2).png)
![](img/image20.png)

Ara configurarem el directori. Per això, dins de l’apartat “Preferències del servidor”, introduirem la configuració que es mostra a la imatge següent

![](img/image21.png)

A continuació, a l’apartat “Ajustos d’eines”, aplicarem la configuració següent

![](img/image22.png)

Després configurarem els usuaris i grups, seguint la configuració indicada a la imatge

![](img/image23.png)

Un cop fet això, ja podrem iniciar sessió

![](img/image24.png)

La primera vegada que accedim, el sistema ens demanarà permís per crear les unitats organitzatives (OU) d’usuaris i grups

![](img/image25.png)

Ara crearem un grup. Per fer-ho, anirem al menú superior i seleccionarem “Comptes” i després “Grups”.
Un cop dins, farem clic a “Crear grup” i introduirem la informació que vulguem afegir.

![](img/image26.png)
![](img/image27.png)
![](img/image28.png)

Ara crearem un usuari. Per fer-ho, anirem al menú superior i seleccionarem “Comptes” i després “Usuaris”.
Un cop dins, farem clic a “Crear usuari” i introduirem la informació que vulguem afegir.

![](img/image29.png)
![](img/image31.png)
![](img/image33.png)

Per ultim li posarem una contrasenya als usuaris per fer això anirem a establir contrasenya i en alla posarem la contrasenya q volguem

![](img/image34.png)

# INTEGRACIÓ CLIENT




