# T07: Instal·lant un servidor de noms 
---
## Configuració de la màquina virtual

Primer de tot he posat 4 GB de RAM

![](img/image01.png)

Despres he configurat els dos adaptadors, he deixat el primer en NAT i el segon le posat en adaptador pont

![](img/image06.png)
![](img/image07.png)

## Configuració de previes servidor
Per configurar entrerem en el arxiu de:
```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

Després posarem manualment la configuració DNS.

![](img/image08.png)
