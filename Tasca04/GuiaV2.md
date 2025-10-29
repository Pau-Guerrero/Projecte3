# Configuració de la Màquina Virtual

Per configurar la màquina virtual, he assignat **4096 MB de RAM**:

![Configuració de RAM](img/image1.png)

## Configuració de Xarxa

- **Primer adaptador:** Xarxa NAT  
  ![Primer adaptador](img/image2.png)

- **Segon adaptador:** Adaptador de només l’amfitrió  
  ![Segon adaptador](img/image3.png)

## Configuració de Netplan

Entrarem a l’arxiu `/etc/netplan/50-cloud-init.yaml` amb `sudo nano` i posarem la següent configuració:

![Netplan](img/image4.png)

## Configuració del Domini

Per configurar el domini, obrirem l’arxiu `/etc/hosts` amb `sudo nano` i modificarem el domini que està després del `127.0.1.1`:

![Hosts 1](img/image5.png)  
![Hosts 2](img/image6.png)  
![Hosts 3](img/image7.png)
