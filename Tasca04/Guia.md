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
