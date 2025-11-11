# T03: Gestió flexible de discos (LVM i Espais d’emmagatzematge)

## Breu descripció
Un cop superada la fase de formació, ja esteu preparats per afrontar el repte dels nostres clients. Tenim un nou i important client, el bufet d’advocats **Garriga i Associats**, un dels més prestigiosos de la ciutat. Gestiona una gran quantitat d'informació legal sensible, per la qual cosa la **integritat, la disponibilitat (alta redundància)** i la **facilitat de gestió** del seu emmagatzematge són d'importància crítica.

La direcció de "Garriga i Associats" ha expressat la necessitat urgent de renovar els seus sistemes de servidors per garantir que la informació estigui protegida contra fallades de disc i que l'espai pugui ser ampliat sense interrupcions.

Com a tècnics d'EverPia, teniu l'encàrrec de **dissenyar i documentar solucions d'emmagatzematge** que compleixin aquests requisits tant en entorns Linux com Windows. Aquest disseny permetrà presentar al client una proposta de solució.

L'objectiu principal és dissenyar i documentar dues solucions d'emmagatzematge (una per servidors Linux i una per servidors Windows) que compleixin amb els principis d'**alta disponibilitat, redundància i escalabilitat** per al client. Com ha de ser una prova de concepte, no treballareu amb servidors reals, sinó amb **màquines virtuals** per documentar els procediments.

---

## 1. Part Linux: LVM amb Zorin OS
S'ha d'utilitzar la distribució **Zorin OS** (o una alternativa Linux compatible) per demostrar la utilitat del **Logical Volume Manager (LVM)**.

### Requisits de la Implementació i Demostració
- **Configuració Inicial:** Crear un grup de volums (VG) i un volum lògic (LV) amb almenys dos discs durs simulats de 10 GB. El volum ha d’estar formatat i muntat automàticament amb `/etc/fstab`.
- **Alta Disponibilitat:** Implementar un **mirall (lvm_mirror)** que protegeixi la informació davant la fallada d'un disc.
- **Instantànies (snapshots):** Afegir dos discos de 10 GB al grup de volums. Crear un volum `lvm_dades`, formatar-lo i muntar-lo. Afegir arxius i usar el segon disc per crear un **snapshot (lv_snapshot)** documentant la restauració en cas de fallada.
- **Escalabilitat:** Ampliar el volum `lv_dades` amb l’espai lliure dins el grup de volums.

---

## 2. Part Windows: Espais d'Emmagatzematge (Storage Spaces)
S'ha d'utilitzar **Windows 11** per demostrar les configuracions amb **Storage Spaces**.

### Requisits de la Implementació i Demostració
- **Configuració inicial:** Crear un **Storage Pool** amb tres discos simulats de 10 GB.
- **Estudi de configuracions:**
  - **Resiliència de Mirall (Mirroring):** Usar dos discos i comprovar alta disponibilitat.
  - **Resiliència de Paritat (Parity):** Explicar l’eficiència d’espai respecte al mirall, usant els tres discos.
  - **Mirall triple:** Afegir discos segons sigui necessari per demostrar major protecció.
- **Demostració de la gestió:** Visualitzar l’estat dels discos i del pool des de la consola de Windows.

---

## Com treballareu i què lliurareu
- Treball en **grup**, dividit en dos equips: Linux (LVM) i Windows (Storage Spaces).
- Cada membre prepara un **guió de la tasca**, cercant comandes i documentació.
- Cada parella realitza la seva **demostració**.
- Revisió conjunta de la documentació i pujada al **repositori** del grup.
- La documentació dels dos casos s’ha de fer en **Markdown**, incloent imatges i explicacions, dins d’una carpeta `tasca03`.
- L’arxiu `README.md` ha de contenir:
  - Descripció de la tasca.
  - Enllaços per accedir als dos documents (Linux i Windows).

> La nota és **conjunta**, per tant és important la comunicació interna.

Posteriorment, haureu de presentar al client les **conclusions de la feina** en una presentació conjunta.


