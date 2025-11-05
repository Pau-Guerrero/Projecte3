# Configuració de la Màquina Virtual

Per configurar la màquina virtual, he assignat **4096 MB de RAM**:

![Configuració de RAM](img/image1.png) <br><br><br>

## Configuració de Xarxa

- **Primer adaptador:** Xarxa NAT  
  ![Primer adaptador](img/image2.png)

- **Segon adaptador:** Adaptador de només l’amfitrió  
  ![Segon adaptador](img/image3.png)<br><br><br>

## Configuració de Netplan

Entrarem a l’arxiu `/etc/netplan/50-cloud-init.yaml` amb `sudo nano` i posarem la següent configuració:

![Netplan](img/image4.png)<br><br><br>

## Configuració del Domini

Per configurar el domini, obrirem l’arxiu `/etc/hosts` amb `sudo nano` i modificarem el domini que està després del `127.0.1.1`:

![Hosts 1](img/image5.png)  
![Hosts 2](img/image6.png)  
![Hosts 3](img/image7.png)<br><br><br><br><br><br><br><br><br>


# Instal·lació i Configuració d’OpenLDAP

Per instal·lar OpenLDAP, primer ens posem com a **root** amb:

```bash
sudo su
```
Després, instal·lem OpenLDAP i les utilitats necessàries:
```bash
apt install slapd ldap-utils -y
```

![](img/image8.png)

Durant la instal·lació, apareixerà aquesta finestra per introduir la contrasenya de l’usuari administrador:

![](img/image9.png)

Per verificar que el servei està funcionant correctament:
```bash
systemctl status slapd
```
![](img/image10.png)<br><br><br>

## Configuració del Domini

Per configurar el domini, executem:
```bash
sudo su
dpkg-reconfigure slapd
```
![](img/image11.png)
![](img/image12.png)

Per comprovar que la configuració s’ha aplicat correctament:
```bash
slapcat
```
![](img/image13.png)<br><br><br><br><br><br><br><br><br>



# LDAP Account Manager (LAM)

## 1. Instal·lació

Primer, instal·lem el paquet del gestor **LDAP Account Manager**:

![Instal·lació LAM](img/image18.png)

Per accedir a LAM, obrim el navegador i escrivim:
http://la nostra IP/lam


Això ens portarà a la pàgina principal on podrem iniciar sessió:

![Pantalla inicial LAM](img/image19.png)<br><br><br>

---

## 2. Configuració inicial de LAM

Abans d’iniciar sessió, hem de configurar LAM:

1. Anem a la part superior dreta i fem clic a **"Configuració de LAM"**.
2. Seleccionem **"Editar perfils del servidor"**:

![Editar perfils 1](img/image20(2).png)  
![Editar perfils 2](img/image20.png)

### Configuració del directori

Dins **"Preferències del servidor"**, introduïm la configuració indicada:

![Preferències del servidor](img/image21.png)

### Ajustos d’eines

A l’apartat **"Ajustos d’eines"**, apliquem la configuració mostrada:

![Ajustos d’eines](img/image22.png)

### Configuració d’usuaris i grups

Seguim la configuració indicada a la imatge:

![Usuaris i grups](img/image23.png)

Un cop fet això, ja podem iniciar sessió:

![Iniciar sessió](img/image24.png)

> La primera vegada que accedim, el sistema ens demanarà permís per crear les unitats organitzatives (OU) d’usuaris i grups:

![Permís OU](img/image25.png)<br><br><br>

---

## 3. Creació de grups

1. Anem al menú superior i seleccionem **"Comptes" > "Grups"**.
2. Fem clic a **"Crear grup"** i introduïm la informació desitjada:

![Crear grup 1](img/image26.png)  
![Crear grup 2](img/image27.png)  
![Crear grup 3](img/image28.png)<br><br><br>

---

## 4. Creació d’usuaris

1. Anem al menú superior i seleccionem **"Comptes" > "Usuaris"**.
2. Fem clic a **"Crear usuari"** i introduïm la informació necessària:

![Crear usuari 1](img/image29.png)  
![Crear usuari 2](img/image31.png)  
![Crear usuari 3](img/image33.png)<br><br><br>

---

## 5. Assignar contrasenya

Per assignar una contrasenya als usuaris:

1. Anem a **"Establir contrasenya"**.
2. Introduïm la contrasenya que vulguem:

![Establir contrasenya](img/image34.png)<br><br><br><br><br><br><br><br><br>

# INTEGRACIÓ CLIENT
### Editar el fitxer `/etc/hosts`

Primer, entrem al directori i editem el fitxer:

```bash
sudo nano /etc/hosts
```

A la IP 127.0.1.1, escrivim el domini del client.

A la IP del servidor (192.168.56.101), escrivim el domini del servidor.

![](img/image35.png)

### Comprovació de configuració del domini

Per verificar que tot funciona correctament:

```bash
hostname -f
```

Aquesta comanda hauria de mostrar el domini del client que hem afegit.

Després comprovem el domini del servidor amb:

```bash
dig (domini_del_servidor)
```

Ens hauria d’aparèixer informació relacionada amb aquest domini.
![](img/image36.png)

### Instal·lació dels mòduls LDAP

Ara instal·larem els paquets necessaris per utilitzar libpam i nss:

```bash
sudo apt install libnss-ldap libpam-ldap ldap-utils nscd -y
```

Seguidament, seguim els passos que apareixeran durant la instal·lació.

![](img/image52.png)
![](img/image38.png)
![](img/image39.png)
![](img/image40.png)
![](img/image41.png)
![](img/image42.png)
![](img/image43.png)

### Comprovació amb ldapsearch

Fem una prova per comprovar la connexió amb el servidor LDAP:

```bash
ldapsearch -x -D 'cn=admin,dc=innovatech09,dc=test' -W -H ldap://server.waytoit.test -b 'dc=innovatech09,dc=test' objectClass=posixAccount uid
```

![](img/image44.png)


### Configuració del fitxer nsswitch.conf

Editem el fitxer:

```bash
sudo nano /etc/nsswitch.conf
```
Afegim ldap a les tres primeres línies corresponents (passwd, group, shadow).

![](img/image45.png)


### Edició del fitxer common-password

Obrim el fitxer següent:

```bash
sudo nano /etc/pam.d/common-password
```

Eliminem la línia que contingui el terme use_authtok.

![](img/image46.png)

### Edició del fitxer common-session

Ara editem:

```bash
sudo nano /etc/pam.d/common-session
```

Afegim una línia per crear automàticament els perfils dels usuaris.

![](img/image47.png)

### Reinici del servei i comprovació d’usuaris

Reiniciem el servei:

```bash
sudo systemctl restart nscd
```

Després comprovem si detecta els usuaris LDAP:

```bash
getent passwd | tail
```

![](img/image48.png)

### Edició del fitxer gdm-launch-environment

Finalment, obrim:

```bash
sudo nano /etc/pam.d/gdm-launch-environment
```

I afegim la primera línia necessària per la configuració.

![](img/image49.png)


### Prova d'accès final

Iniciem sessió amb la conta que vem crear amb el account manager LAM

![](img/image50.png)

I per saber la creació automàtica de la carpeta personal posarem:

```bash
id
```
