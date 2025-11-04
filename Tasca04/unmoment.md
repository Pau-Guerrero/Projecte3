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

![](img/image37.png)
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
